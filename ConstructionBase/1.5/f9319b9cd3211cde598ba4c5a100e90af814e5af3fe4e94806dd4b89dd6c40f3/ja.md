# ConstructionBase

[![Stable](https://img.shields.io/badge/docs-stable-blue.svg)](https://JuliaObjects.github.io/ConstructionBase.jl/stable) [![Dev](https://img.shields.io/badge/docs-dev-blue.svg)](https://JuliaObjects.github.io/ConstructionBase.jl/dev) [![Build Status](https://github.com/JuliaObjects/ConstructionBase.jl/workflows/CI/badge.svg)](https://github.com/JuliaObjects/ConstructionBase.jl/actions?query=workflow%3ACI) [![GitHub stars](https://img.shields.io/github/stars/JuliaObjects/ConstructionBase.jl?style=social)](https://github.com/JuliaObjects/ConstructionBase.jl)

ConstructionBaseは、オブジェクトの構築のための基本的な関数を提供する非常に軽量なパッケージです：

```julia
setproperties(obj::MyType, patch::NamedTuple)
constructorof(MyType)
```

これらの関数はオーバーロード可能であり、そのようにすることで以下のパッケージとの相互運用性が提供されます：

  * [Flatten.jl](https://github.com/rafaqz/Flatten.jl)
  * [Setfield.jl](https://github.com/jw3126/Setfield.jl)
  * [BangBang.jl](https://github.com/tkf/BangBang.jl)
  * [Accessors.jl](https://github.com/JuliaObjects/Accessors.jl)
  * [ModelParameters.jl](https://github.com/rafaqz/ModelParameters.jl)
