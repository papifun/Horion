cmake_minimum_required(VERSION 3.12)
project(Nofine)

set(CMAKE_CXX_STANDARD 17)

if (CMAKE_CXX_COMPILER_ID STREQUAL "Clang")
    add_compile_options(-Wno-dynamic-class-memaccess -Wno-microsoft-goto -Wno-delete-incomplete /EHsc /Ob1)
elseif (CMAKE_CXX_COMPILER_ID STREQUAL "MSVC")
    add_compile_options(/MP /Ob1)
endif()

add_compile_definitions(WIN32_LEAN_AND_MEAN)
add_compile_definitions(NOMINMAX)
if(CMAKE_BUILD_TYPE MATCHES Release)

elseif(CMAKE_BUILD_TYPE MATCHES BetaConf)
    add_compile_definitions(_BETA)
endif()

include_directories(.)
include_directories(include)
include_directories(include/glm/)

link_directories(minhook)

add_library(Horion SHARED
        Horion/Command/Commands/BindCommand.cpp
        Horion/Command/Commands/BindCommand.h
        Horion/Command/Commands/ConfigCommand.cpp
        Horion/Command/Commands/ConfigCommand.h
        Horion/Command/Commands/FriendListCommand.cpp
        Horion/Command/Commands/FriendListCommand.h
        Horion/Command/Commands/NameSpoofCommand.cpp
        Horion/Command/Commands/NameSpoofCommand.h
        Horion/Command/Commands/PanicCommand.cpp
        Horion/Command/Commands/PanicCommand.h

        Horion/Command/Commands/UnbindCommand.cpp
        Horion/Command/Commands/UnbindCommand.h
        Horion/Config/AccountInformation.cpp
        Horion/Config/AccountInformation.h
        Horion/Config/ConfigManager.cpp
        Horion/Config/ConfigManager.h
        Horion/FriendList/FriendList.cpp
        Horion/FriendList/FriendList.h
        Horion/Menu/ClickGui.cpp
        Horion/Menu/ClickGui.h
        Horion/Menu/TabGui.cpp
        Horion/Menu/TabGui.h
        Horion/Module/Modules/AutoSneak.cpp
        Horion/Module/Modules/AutoSneak.h
        Horion/Module/Modules/AutoSprint.cpp
        Horion/Module/Modules/AutoSprint.h
        Horion/Module/Modules/ChestESP.cpp
        Horion/Module/Modules/ChestESP.h
        Horion/Module/Modules/ChestStealer.cpp
        Horion/Module/Modules/ChestStealer.h
        Horion/Module/Modules/ClickGuiMod.cpp
        Horion/Module/Modules/ClickGuiMod.h
        Horion/Module/Modules/Freecam.cpp
        Horion/Module/Modules/Freecam.h
        Horion/Module/Modules/FullBright.cpp
        Horion/Module/Modules/FullBright.h
        Horion/Module/Modules/HudModule.cpp
        Horion/Module/Modules/HudModule.h
        Horion/Module/Modules/InventoryCleaner.cpp
        Horion/Module/Modules/InventoryCleaner.h
        Horion/Module/Modules/InventoryMove.cpp
        Horion/Module/Modules/InventoryMove.h
        Horion/Module/Modules/Module.cpp
        Horion/Module/Modules/Module.h
        Horion/Module/Modules/NameTags.cpp
        Horion/Module/Modules/NameTags.h
        Horion/Module/Modules/NightMode.cpp
        Horion/Module/Modules/NightMode.h
        Horion/Module/Modules/NoFriends.cpp
        Horion/Module/Modules/NoFriends.h
        Horion/Module/Modules/NoSwing.cpp
        Horion/Module/Modules/NoSwing.h
        Horion/Module/Modules/RainbowSky.cpp
        Horion/Module/Modules/RainbowSky.h
        Horion/Module/Modules/StackableItem.cpp
        Horion/Module/Modules/StackableItem.h
        Horion/Module/Modules/Tracer.cpp
        Horion/Module/Modules/Tracer.h
        Horion/Module/Modules/Xray.cpp
        Horion/Module/Modules/Xray.h
        Horion/Module/Modules/Zoom.cpp
        Horion/Module/Modules/Zoom.h

        Horion/Scripting/Functions/CommandManagerFunctions.cpp
        Horion/Scripting/Functions/CommandManagerFunctions.h
        Horion/Scripting/Functions/EntityFunctions.cpp
        Horion/Scripting/Functions/EntityFunctions.h
        Horion/Scripting/Functions/GameFunctions.cpp
        Horion/Scripting/Functions/GameFunctions.h
        Horion/Scripting/Functions/GlobalFunctions.cpp
        Horion/Scripting/Functions/GlobalFunctions.h
        Horion/Scripting/Functions/HorionFunctions.cpp
        Horion/Scripting/Functions/HorionFunctions.h
        Horion/Scripting/Functions/LocalPlayerFunctions.cpp
        Horion/Scripting/Functions/LocalPlayerFunctions.h
        Horion/Scripting/Functions/ModuleManagerFunctions.cpp
        Horion/Scripting/Functions/ModuleManagerFunctions.h
        Horion/Scripting/Functions/Vector3Functions.cpp
        Horion/Scripting/Functions/Vector3Functions.h
        Horion/Scripting/JsScriptModule.cpp
        Horion/Scripting/JsScriptModule.h
        Horion/Scripting/ScriptInstance.cpp
        Horion/Scripting/ScriptInstance.h
        Horion/Scripting/ScriptManager.cpp
        Horion/Scripting/ScriptManager.h
        Horion/DrawUtils.cpp
        Horion/DrawUtils.h
        Horion/GuiUtils.cpp
        Horion/GuiUtils.h
        Horion/ImmediateGui.cpp
        Horion/ImmediateGui.h
        Horion/Loader.cpp
        Horion/Loader.h
        resource.h SDK/TextHolder.cpp SDK/CChestBlockActor.cpp SDK/Tag.cpp Utils/keys.h SDK/CBlockLegacy.cpp SDK/CItem.cpp SDK/CInventory.cpp SDK/CInventoryTransaction.cpp SDK/CEntity.cpp SDK/CComplexInventoryTransaction.cpp SDK/CPacket.cpp SDK/CMinecraftUIRenderContext.cpp SDK/CClientInstance.cpp SDK/CMoveInputHandler.cpp SDK/CImageBuffer.h Horion/Module/Modules/Freelook.cpp Horion/Module/Modules/Freelook.h SDK/CCamera.h SDK/CCamera.cpp Horion/Module/Modules/NoHurtcam.cpp Horion/Module/Modules/NoHurtcam.h Horion/Module/Modules/AntiImmobile.cpp Horion/Module/Modules/AntiImmobile.h Horion/path/JoePathFinder.cpp Horion/path/JoePathFinder.h Horion/path/JoePath.cpp Horion/path/JoePath.h Horion/path/JoeSegment.cpp Horion/path/JoeSegment.h Horion/path/JoeMovementController.cpp Horion/path/JoeMovementController.h Horion/path/goals/JoeGoal.cpp Horion/path/goals/JoeGoal.h Horion/path/goals/JoeGoalXYZ.cpp Horion/path/goals/JoeGoalXYZ.h Horion/path/goals/JoeGoalXZ.cpp Horion/path/goals/JoeGoalXZ.h Horion/path/JoeConstants.h Horion/path/goals/JoeGoalY.cpp Horion/path/goals/JoeGoalY.h Horion/Module/Modules/FollowPathModule.cpp Horion/Module/Modules/FollowPathModule.h Horion/Command/Commands/PathCommand.cpp Horion/Command/Commands/PathCommand.h Horion/path/JoeConstants.cpp Horion/Scripting/Functions/LevelFunctions.cpp Horion/Scripting/Functions/LevelFunctions.h Horion/Scripting/Functions/DrawFunctions.cpp Horion/Scripting/Functions/DrawFunctions.h "Horion/Module/Modules/Twerk.cpp" "Horion/Module/Modules/Twerk.h")
