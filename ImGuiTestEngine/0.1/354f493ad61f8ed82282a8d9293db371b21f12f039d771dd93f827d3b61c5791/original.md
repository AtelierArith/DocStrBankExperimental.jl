```julia
primitive type RunSpeed <: Enum{Int32} 32
```

Wrapper around the upstream `ImGuiTestRunSpeed`. Possible values:

  * `RunSpeed_Fast`
  * `RunSpeed_Normal`
  * `RunSpeed_Cinematic`
