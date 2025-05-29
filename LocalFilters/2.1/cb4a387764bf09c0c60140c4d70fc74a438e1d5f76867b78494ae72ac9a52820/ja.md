```
convolve(A, B=3)
```

は、配列 `A` と `B` で定義されたカーネルの離散畳み込みを生成します。結果 `dst` は `A` に似た配列です。

`Idx(A)` を配列 `A` の有効なインデックスの集合を示すために使用し、`B` が値の配列であると仮定すると、`A` と `B` の離散畳み込みは次のように書かれます：

```
dst = similar(A, T)
for i ∈ Idx(dst)
    v = zero(T)
    @inbounds for j ∈ Idx(A) ∩ (i - Idx(B))
        v += A[j]*B[i-j]
    end
    dst[i] = v
end
```

ここで `T` は `A` と `B` の要素の積の和の型であり、`Idx(A) ∩ (i - Idx(B))` は `j` のインデックスの部分集合を示します。これは `j ∈ Idx(A)` かつ `i - j ∈ Idx(B)` であり、したがって `A[j]` と `B[i-j]` が有効であることを意味します。

[`convolve!`](@ref) および [`localfilter!`](@ref) も参照してください。
