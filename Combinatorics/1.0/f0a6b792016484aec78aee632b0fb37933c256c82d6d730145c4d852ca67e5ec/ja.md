```
parity(p)
```

順列 `p` のパリティを [`levicivita`](@ref) 関数を使用して計算し、`iseven(parity(p))` のような呼び出しを許可します。`p` が順列でない場合はエラーがスローされます。

# 例

```jldoctest
julia> parity([1, 2, 3])
0

julia> parity([3, 2, 1])
1

julia> parity([1, 1, 1])
ERROR: ArgumentError: Not a permutation
[...]

julia> parity((collect(1:100)))
0
```
