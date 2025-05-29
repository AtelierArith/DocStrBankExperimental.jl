```julia
mutable struct MLorentzVector{T} <: QEDbase.AbstractLorentzVector{T}
```

具体的な可変ローレンツベクトルの実装です。自己完結していない具体的な実装の各操作（すなわち、同じローレンツベクトル型を生成するもの）は、この型の結果になります。

# フィールド

  * `t::Any`: `t` コンポーネント
  * `x::Any`: `x` コンポーネント
  * `y::Any`: `y` コンポーネント
  * `z::Any`: `z` コンポーネント
