```
distinct(xs)
```

すでに遭遇した値をスキップしながら値を反復処理します。

```jldoctest
julia> for i in distinct([1,1,2,1,2,4,1,2,3,4])
           @show i
       end
i = 1
i = 2
i = 4
i = 3
```
