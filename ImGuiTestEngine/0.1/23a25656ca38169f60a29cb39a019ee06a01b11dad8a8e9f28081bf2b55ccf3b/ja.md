```julia
primitive type TestVerboseLevel <: Enum{Int32} 32
```

上流の `ImGuiTestVerboseLevel` のラッパー。可能な値：

  * `TestVerboseLevel_Silent`
  * `TestVerboseLevel_Error`
  * `TestVerboseLevel_Warning`
  * `TestVerboseLevel_Info`
  * `TestVerboseLevel_Debug`
  * `TestVerboseLevel_Trace`
