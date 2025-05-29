```
hg(x, y, z=zero(eltype(x)); θ=zero(eltype(x)), m=0, n=0, w=one(eltype(x)), k=one(eltype(x)))
```

エルミート-ガウスモードを計算します。

`x`、`y`、および `z` は数値またはベクトルであり得ますが、`x` と `y` は常に同じ種類でなければなりません。

# その他の引数:

  * `m`: x インデックス
  * `n`: y インデックス
  * `w`: ビームのウエスト
  * `k`: 波数

# 例

```jldoctest
rs = LinRange(-5, 5, 256)
zs = LinRange(0, 1, 32)

# x と y のみ
ψ₁ = hg(rs, rs, m=3, n=2)
ψ₂ = [hg(x, y, m=3, n=2) for x in rs, y in rs]

# x、y、および z
ψ₃ = hg(rs, rs, zs, m=3, n=2)
ψ₄ = [hg(x, y, z, m=3, n=2) for x in rs, y in rs, z ∈ zs]

ψ₁ ≈ ψ₂ && ψ₃ ≈ ψ₄

# 出力

true
```

さらに [`diagonal_hg`](@ref)、[`lg`](@ref) を参照してください。
