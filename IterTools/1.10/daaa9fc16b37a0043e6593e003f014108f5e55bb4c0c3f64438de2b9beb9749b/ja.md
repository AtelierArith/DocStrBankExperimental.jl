```
ncycle(iter, n)
```

`iter`を`n`回サイクルします。

```jldoctest
julia> for i in ncycle(1:3, 2)
           @show i
       end
i = 1
i = 2
i = 3
i = 1
i = 2
i = 3
```
