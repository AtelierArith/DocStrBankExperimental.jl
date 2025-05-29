```
to_pauli(bsf::AbstractVecOrMat{Bool}) -> Union{String,Vector{String}}
```

バイナリシンプレクティック形式をパウリ文字列演算子に変換します。

ベクトルは単一のパウリ文字列に変換されます。行列は行ごとにパウリ文字列のコレクションに変換されます。

# 例

```jldoctest
julia> to_pauli(BitVector([1, 0, 0, 0, 1, 0, 0, 1, 0, 1]))
"XIZIY"
```

```jldoctest
julia> to_pauli(BitMatrix([1 0 0 0 1 0 0 1 0 1; 0 1 0 1 0 0 0 1 1 0]))
2-element Vector{String}:
 "XIZIY"
 "IXZYI"
```
