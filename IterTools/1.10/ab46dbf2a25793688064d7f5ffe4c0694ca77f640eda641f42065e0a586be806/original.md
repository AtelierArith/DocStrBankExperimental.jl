```
groupby(f, xs)
```

Group consecutive values that share the same result of applying `f`.

```jldoctest
julia> for i in groupby(x -> x[1], ["face", "foo", "bar", "book", "baz", "zzz"])
           @show i
       end
i = ["face", "foo"]
i = ["bar", "book", "baz"]
i = ["zzz"]
```
