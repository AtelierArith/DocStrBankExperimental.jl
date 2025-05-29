```
tensor(A, B)
A ⊗ B
```

`A`と`B`のテンソル積を計算します。もし`C = A ⊗ B`であれば、`C[i1, ..., im, j1, ..., jn] = A[i1, ... im] * B[j1, ..., jn]`です。

ベクトル`v`と`w`に対して、クロネッカー積はテンソル積に関連しており、`kron(v,w) == vec(w ⊗ v)`または`w ⊗ v == reshape(kron(v,w), (length(w), length(v)))`です。

# 例

```jldoctest; setup=:(using TensorCore)
julia> a = [2, 3]; b = [5, 7, 11];

julia> a ⊗ b
2×3 Array{Int64,2}:
 10  14  22
 15  21  33
```

`tensor!(Y,A,B)`も参照してください。
