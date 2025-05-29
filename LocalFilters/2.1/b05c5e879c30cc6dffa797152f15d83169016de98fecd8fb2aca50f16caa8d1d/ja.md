```
correlate(A, B=3) -> dst
```

は、配列 `A` の離散相関を、`B` によって定義されたカーネルで計算します。結果 `dst` は `A` に似た配列です。

配列 `A` の有効なインデックスの集合を `Idx(A)` とし、`B` が数値の配列であると仮定すると、`A` と `B` の離散畳み込みは次のように書かれます：

```
dst = similar(A, T)
for i ∈ Idx(dst)
    v = zero(T)
    @inbounds for j ∈ Idx(A) ∩ (i + Idx(B))
        v += A[j]*B[j-i]
    end
    dst[i] = v
end
```

ここで `T` は `A` と `B` の要素の積の和の型であり、`Idx(A) ∩ (i + Idx(B))` は `j` のインデックスの部分集合を示します。これは `j ∈ Idx(A)` かつ `j - i ∈ Idx(B)` であり、したがって `A[j]` と `B[j-i]` が有効であることを意味します。

[`correlate!`](@ref) および [`convolve`](@ref) も参照してください。
