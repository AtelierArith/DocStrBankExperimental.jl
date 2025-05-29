function find*full*indices(N, dim)

```
i1 >= i2 >= i3 ... >= i{dim} となるインデックスのタプル (i1, i2, i3, ..., i{dim}) の順序付き配列を返します。これは、SymmetricTensor{T, N, dim} の線形インデックスに対応する直交インデックスを見つけるために使用できます。
例:
julia> find_full_indices(3, 3)
10-element Vector{Tuple{Int8, Int8, Int8}}:
(1, 1, 1)
(2, 1, 1)
(3, 1, 1)
(2, 2, 1)
(3, 2, 1)
(3, 3, 1)
(2, 2, 2)
(3, 2, 2)
(3, 3, 2)
(3, 3, 3)

これは生成関数で実装されており、dim = 3 の場合、次のコードが実行されます:
function _find_full_indices(N, Val(3))
    full_indices = NTuple{3, Int16}[]
    for i3 = 1:N
        for i2 = i3:N
            for i1 = i2:N
                push!(full_indices, ((i1..., i2)..., i3))
            end
        end
    end
    full_indices
end
```
