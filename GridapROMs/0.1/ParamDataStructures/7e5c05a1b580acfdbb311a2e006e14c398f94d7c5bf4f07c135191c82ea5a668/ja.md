```
struct ParamFunction{F,P} <: AbstractParamFunction{P}
  fun::F
  params::P
end
```

パラメトリック空間のドメインを持つパラメトリック関数の表現。関数 `f` : Ω₁ × ... × Ωₙ × D が与えられたとき、ここで D は `ParamSpace` であり、`μ ∈ D` における `f` の評価は、Ω₁ × ... × Ωₙ に対する `f` の制限を返します。
