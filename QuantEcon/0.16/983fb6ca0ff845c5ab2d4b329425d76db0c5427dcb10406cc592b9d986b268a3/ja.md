```
next_k_array!(a)
```

k個の異なる正の整数からなる配列`a`が昇順にソートされている場合、要素の降順列の辞書順での次のk-arrayを返します。これは[組合せ数体系](https://en.wikipedia.org/wiki/Combinatorial_number_system)に従います。`a`はその場で変更されます。

# 引数

  * `a::Vector{<:Integer}`: 長さkの配列。

# 戻り値

  * `a::Vector{<:Integer}`: `a`のビュー。

# 例

```julia
julia> n, k = 4, 2;

julia> a = collect(1:2);

julia> while a[end] <= n
           @show a
           next_k_array!(a)
       end
a = [1, 2]
a = [1, 3]
a = [2, 3]
a = [1, 4]
a = [2, 4]
a = [3, 4]
```
