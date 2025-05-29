```julia
primitive type TestVerboseLevel <: Enum{Int32} 32
```

Wrapper around the upstream `ImGuiTestVerboseLevel`. Possible values:

  * `TestVerboseLevel_Silent`
  * `TestVerboseLevel_Error`
  * `TestVerboseLevel_Warning`
  * `TestVerboseLevel_Info`
  * `TestVerboseLevel_Debug`
  * `TestVerboseLevel_Trace`
