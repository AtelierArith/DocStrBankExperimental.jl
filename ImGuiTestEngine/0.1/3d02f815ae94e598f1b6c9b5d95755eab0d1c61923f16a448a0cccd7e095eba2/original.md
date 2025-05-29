```julia
struct CxxRef{ImGuiTestEngine.lib.ImGuiTestEngineIO} <: CxxWrap.CxxWrapCore.CxxBaseRef{ImGuiTestEngine.lib.ImGuiTestEngineIO}
```

A wee typedef for `ImGuiTestEngineIO`. Get this from an [`Engine`](@ref) with [`GetIO()`](@ref).

Supported properties:

  * `ConfigSavedSettings::Bool`
  * `ConfigRunSpeed::`[`RunSpeed`](@ref)
  * `ConfigStopOnError::Bool`
  * `ConfigKeepGuiFunc::Bool`
  * `ConfigVerboseLevel::`[`TestVerboseLevel`](@ref)
  * `ConfigVerboseLevelOnError::`[`TestVerboseLevel`](@ref)
  * `ConfigRestoreFocusAfterTests::Bool`
  * `ConfigCaptureEnabled::Bool`
  * `ConfigCaptureOnError::Bool`
  * `ConfigNoThrottle::Bool`
  * `ConfigMouseDrawCursor::Bool`
  * `IsRunningTests::Bool` (readonly)

!!! danger
    This a memory-unsafe type, only use it while the engine is alive.

