```
Deferred
```

必要なときにのみ、一度だけ計算される値を表す構造体です。

これは、使用されるかどうかわからない `struct` の高コストなメンバーを計算するのに最も便利です。計算を遅延させることで、データが決して使用されない場合はコストを回避できます。

`Deferred` は、必要なときに必要なデータが利用可能であることを保証するためにクロージャを利用します。`Deferred` はスレッドセーフです。

# 例:

```julia-repl
julia> using Procrastinate
julia> d = Deferred() do
    # 一部の高コストな計算
    println("計算中!")
    return "結果"
end
julia> d()
計算中!
"結果"
julia> d()
"結果"
```
