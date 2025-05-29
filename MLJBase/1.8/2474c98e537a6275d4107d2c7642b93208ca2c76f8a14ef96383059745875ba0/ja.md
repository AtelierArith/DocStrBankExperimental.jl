```
recursive_getproperty(object, nested_name::Expr)
```

`object`に対して`getproperty`を再帰的に呼び出して、いくつかのネストされたプロパティの値を抽出します。以下の例のように：

```julia-repl
julia> object = (X = (x = 1, y = 2), Y = 3);
julia> recursive_getproperty(object, :(X.y))
2
```
