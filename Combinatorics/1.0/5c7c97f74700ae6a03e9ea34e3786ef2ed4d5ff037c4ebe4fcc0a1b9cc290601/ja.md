```
nthperm(p)
```

生成された順列 `p` を生成した整数 `k` を返します。`1 <= k <= factorial(n)` の場合、`nthperm(nthperm([1:n], k)) == k` であることに注意してください。

# 例

```jldoctest
julia> nthperm(nthperm([1:3...], 4))
4

julia> collect(permutations([1, 2, 3]))
6-element Vector{Vector{Int64}}:
 [1, 2, 3]
 [1, 3, 2]
 [2, 1, 3]
 [2, 3, 1]
 [3, 1, 2]
 [3, 2, 1]

julia> nthperm([1, 2, 3])
1

julia> nthperm([3, 2, 1])
6

julia> nthperm([1, 1, 1])
ERROR: ArgumentError: argument is not a permutation
[...]

julia> nthperm(collect(1:10))
1

julia> nthperm(collect(10:-1:1))
3628800
```
