```julia
primitive type RunSpeed <: Enum{Int32} 32
```

上流の `ImGuiTestRunSpeed` のラッパー。可能な値：

  * `RunSpeed_Fast`
  * `RunSpeed_Normal`
  * `RunSpeed_Cinematic`
