```
passmissing(f)
```

引数のいずれかが `missing` の場合に `missing` を返す関数を返します（引数の数や型が `f` に対して定義されたメソッドと一致しなくても）。そうでない場合は、これらの引数に `f` を適用します。

`passmissing` は `f` 関数にキーワード引数を渡すことをサポートしていません。

# 例

```jldoctest
julia> passmissing(sqrt)(4)
2.0

julia> passmissing(sqrt)(missing)
missing

julia> passmissing(sqrt).([missing, 4])
2-element Array{Union{Missing, Float64},1}:
  missing
   2.0

julia> passmissing((x,y)->"$x $y")(1, 2)
"1 2"

julia> passmissing((x,y)->"$x $y")(missing)
missing
```
