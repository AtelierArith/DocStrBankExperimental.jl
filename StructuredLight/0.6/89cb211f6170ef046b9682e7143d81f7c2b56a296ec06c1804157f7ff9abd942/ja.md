```
lg(x, y, z=zero(eltype(x)); p=0, l=0, w=one(eltype(x)), k=one(eltype(x)))
```

対角ハーミート-ガウスモードを計算します。

`x`、`y`、および `z` は数値またはベクトルであり得ますが、`x` と `y` は常に同じ種類でなければなりません。

# その他の引数:

  * `p`: 放射インデックス
  * `l`: トポロジカルチャージ
  * `w`: ビームのウエスト
  * `k`: 波数

# 例

```jldoctest
rs = LinRange(-5, 5, 256)
zs = LinRange(0, 1, 32)

# x と y のみ
ψ₁ = lg(rs, rs, p=1, l=2)
ψ₂ = [lg(x, y, p=1, l=2) for x in rs, y in rs]

# x、y、z の場合
ψ₃ = lg(rs, rs, zs, p=1, l=2)
ψ₄ = [lg(x, y, z, p=1, l=2) for x in rs, y in rs, z ∈ zs]

ψ₃ ≈ ψ₄

# 出力

true
```

さらに [`hg`](@ref) や [`diagonal_hg`](@ref) を参照してください。
