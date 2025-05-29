```
NonlinFitness(fitness::Function)
```

一般的な非線形フィットネス関数を定義するために使用され、目的関数の出力 `y` の品質を測定します。

フィットネス関数が線形の場合は、`LinFitness` を使用すると、より良いパフォーマンスが得られる場合があります。

参照: [`LinFitness`](@ref)

# 例

```julia-repl
julia> NonlinFitness(y -> cos(y[1]) + sin(y[2]))
```
