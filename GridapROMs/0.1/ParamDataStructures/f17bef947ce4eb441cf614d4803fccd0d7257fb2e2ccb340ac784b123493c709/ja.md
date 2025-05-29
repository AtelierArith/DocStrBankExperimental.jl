```
struct TransientParamSpace{P<:ParamSpace,T} <: AbstractSet{TransientRealization}
  parametric_space::P
  temporal_domain::T
end
```

フィールド:

  * `parametric_space`: 基本のパラメータ空間
  * `temporal_domain`: 基本の時間空間

本質的には、`parametric_space` × `temporal_domain` のタプル (p,t) の集合を表します。
