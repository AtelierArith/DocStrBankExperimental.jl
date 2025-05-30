```
EPGStates{T <: Real}
```

3つのベクトル Fp、Fn、Z に EPG 状態を格納します。

# コンストラクタ :

```
EPGStates(Fp::Vector{Complex{S}},Fn::Vector{Complex{S}},Z::Vector{Complex{S}}) where {S <: Real}
EPGStates(Fp::T=0,Fn::T=0,Z::T=1) where T <: Number
```

# フィールド

  * `Fp::Vector{Complex{T}}`
  * `Fn::Vector{Complex{T}}`
  * `Z::Vector{Complex{T}}`

# 関連関数

  * `getStates(E::EPGStates)` : EPG 状態を行列 3xN として抽出します。
