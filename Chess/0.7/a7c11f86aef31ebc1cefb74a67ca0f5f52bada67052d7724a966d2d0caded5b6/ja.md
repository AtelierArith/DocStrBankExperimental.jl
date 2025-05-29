```
isok(f::SquareFile)
```

`SquareFile`が有効な値を含んでいるかどうかをテストします。

# 例

```julia-repl
julia> isok(FILE_A)
true

julia> isok(SquareFile(0))
false
```
