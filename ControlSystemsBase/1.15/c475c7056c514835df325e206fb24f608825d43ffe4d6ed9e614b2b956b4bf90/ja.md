```
StateSpace{TE, T} <: AbstractStateSpace{TE}
```

標準状態空間システムを表すオブジェクトです。

ユーザー向けのコンストラクタとしての関数 [`ss`](@ref) およびドキュメントページ [システムの作成](https://juliacontrol.github.io/ControlSystems.jl/stable/man/creating_systems/) を参照してください。

# フィールド:

  * `A::Matrix{T}`
  * `B::Matrix{T}`
  * `C::Matrix{T}`
  * `D::Matrix{T}`
  * `timeevol::TE`
