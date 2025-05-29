```
ftcall(f::Function, ft::FrankenTuple)
```

関数 `f` を `ft` の無名部分を位置引数として、`ft` の名前付き部分をキーワード引数として呼び出します。

# 例

```jldoctest
julia> ftcall(mapreduce, ftuple(abs2, -, 1:4; init=0))
-30
```
