```
PermutedDimsQuasiArray(A, perm) -> B
```

抽象クワジ配列 `A` が与えられたとき、次元が順序を変えたように見えるビュー `B` を作成します。`permutedims` に似ていますが、コピーは行われません（`B` は `A` とストレージを共有します）。

参照: [`permutedims`](@ref)。

# 例

```jldoctest
julia> A = rand(3,5,4);

julia> B = PermutedDimsQuasiArray(A, (3,1,2));

julia> size(B)
(4, 3, 5)

julia> B[3,1,2] == A[1,2,3]
true
```
