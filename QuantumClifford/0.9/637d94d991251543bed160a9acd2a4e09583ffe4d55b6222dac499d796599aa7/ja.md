与えられたパウリ演算子に関連するクリフォード演算子を与えるシンプレクティック・グラム・シュミット手続きを実行します。

アルゴリズムの詳細は[koenig2014efficiently](@cite)に記載されています。

```jldoctest
julia> symplecticGS(P"X", padded_n=3)
X₁ ⟼ + X__
X₂ ⟼ + _X_
X₃ ⟼ + __X
Z₁ ⟼ + Z__
Z₂ ⟼ + _Z_
Z₃ ⟼ + __Z

julia> symplecticGS(P"Z")
X₁ ⟼ + Z
Z₁ ⟼ + X
```

また、[`enumerate_cliffords`](@ref)や[`clifford_cardinality`](@ref)も参照してください。
