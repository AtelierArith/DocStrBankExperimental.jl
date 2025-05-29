```julia
struct CxxRef{ImGuiTestEngine.lib.ImGuiTestEngineIO} <: CxxWrap.CxxWrapCore.CxxBaseRef{ImGuiTestEngine.lib.ImGuiTestEngineIO}
```

`ImGuiTestEngineIO`のための小さなtypedefです。これを[`Engine`](@ref)から[`GetIO()`](@ref)で取得します。

サポートされているプロパティ：

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
  * `IsRunningTests::Bool` (読み取り専用)

!!! danger
    これはメモリ安全でない型です。エンジンが生きている間だけ使用してください。

