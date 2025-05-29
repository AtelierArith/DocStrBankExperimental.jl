```
partition(xs, n, [step])
```

値を `n`-タプルにグループ化します。

```jldoctest
julia> for i in partition(1:9, 3)
           @show i
       end
i = (1, 2, 3)
i = (4, 5, 6)
i = (7, 8, 9)
```

`step` パラメータが設定されている場合、各タプルは `step` 値で区切られます。

```jldoctest
julia> for i in partition(1:9, 3, 2)
           @show i
       end
i = (1, 2, 3)
i = (3, 4, 5)
i = (5, 6, 7)
i = (7, 8, 9)

julia> for i in partition(1:9, 3, 3)
           @show i
       end
i = (1, 2, 3)
i = (4, 5, 6)
i = (7, 8, 9)

julia> for i in partition(1:9, 2, 3)
           @show i
       end
i = (1, 2)
i = (4, 5)
i = (7, 8)
```
