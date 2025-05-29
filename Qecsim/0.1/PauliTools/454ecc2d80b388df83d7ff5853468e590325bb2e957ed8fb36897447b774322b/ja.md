```
weight(bsf::AbstractVecOrMat{Bool}) -> Int
```

バイナリシンプレクティック形式の重みを返します。

# 例

```jldoctest
julia> weight(BitVector([1, 0, 0, 0, 1, 0, 0, 1, 0, 1]))
3
```

```jldoctest
julia> weight(BitMatrix([1 0 0 0 1 0 0 1 0 1; 1 1 1 1 1 0 0 0 0 0]))
8
```
