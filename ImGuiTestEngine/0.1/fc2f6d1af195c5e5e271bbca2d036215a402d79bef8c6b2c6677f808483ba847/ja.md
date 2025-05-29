```julia
primitive type TestGroup <: Enum{Int32} 32
```

上流の `ImGuiTestGroup` 列挙型のラッパー。可能な値：

  * `TestGroup_Perfs`
  * `TestGroup_Tests`
  * `TestGroup_Unknown`
