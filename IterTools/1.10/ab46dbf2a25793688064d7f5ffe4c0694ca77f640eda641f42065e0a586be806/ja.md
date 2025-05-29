```
groupby(f, xs)
```

同じ `f` を適用した結果を持つ連続する値をグループ化します。

```jldoctest
julia> for i in groupby(x -> x[1], ["face", "foo", "bar", "book", "baz", "zzz"])
           @show i
       end
i = ["face", "foo"]
i = ["bar", "book", "baz"]
i = ["zzz"]
```
