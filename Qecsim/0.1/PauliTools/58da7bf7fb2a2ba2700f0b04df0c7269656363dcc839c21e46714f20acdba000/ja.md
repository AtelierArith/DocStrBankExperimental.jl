```
to_bsf(
    pauli::Union{AbstractString,AbstractVector{<:AbstractString}}
) -> Union{BitVector,BitMatrix}
```

パウリ文字列演算子をバイナリシンプレクティック形式に変換します。

単一のパウリ文字列はベクトルに変換されます。パウリ文字列のベクトルは、各行がパウリに対応する行列に変換されます。

# 例

```jldoctest
julia> to_bsf("XIZIY")
10-element BitVector:
 1
 0
 0
 0
 1
 0
 0
 1
 0
 1
```

```jldoctest
julia> to_bsf(["XIZIY", "IXZYI"])
2×10 BitMatrix:
 1  0  0  0  1  0  0  1  0  1
 0  1  0  1  0  0  0  1  1  0
```
