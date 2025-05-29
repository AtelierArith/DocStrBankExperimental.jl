```julia
primitive type TestGroup <: Enum{Int32} 32
```

Wrapper for the upstream `ImGuiTestGroup` enum. Possible values:

  * `TestGroup_Perfs`
  * `TestGroup_Tests`
  * `TestGroup_Unknown`
