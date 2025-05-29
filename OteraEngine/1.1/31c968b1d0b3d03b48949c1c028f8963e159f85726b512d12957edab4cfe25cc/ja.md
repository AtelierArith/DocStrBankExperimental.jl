```
@filter func
@filter alias func
```

このマクロは `func` を OteraEngine に登録し、その後関数はフィルターとして利用可能になります。`func` の形式は通常の定義または1行の定義である必要がありますが、匿名ではいけません。また、エイリアスを使ってフィルターを定義することもできます。

# 例

```julia-repr
julia> @filter function greet(x)
            return x * "Hello"
        end
julia> @filter hello function greet(x)
            return x * "Hello"
        end
julia> @filter say_twice(x) = x*x
julia> @filter double say_twice(x) = x*x
```

このようにフィルターを定義した後、`greet`、`hello`、`say_twice`、`double` として使用できます。
