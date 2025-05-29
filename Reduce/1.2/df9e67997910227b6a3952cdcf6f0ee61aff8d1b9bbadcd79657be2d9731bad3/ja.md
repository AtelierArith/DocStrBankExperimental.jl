```
rcall{T}(e::T)
```

Reduceインタプリタを使用してJulia式または文字列を評価し、出力を入力型に戻します

## 例

```julia-repl
julia> rcall("int(sin(y)^2, y)")
"( - cos(y)*sin(y) + y)/2"

julia> rcall(:(int(1/(1+x^2), x)))
:(atan(x))
```
