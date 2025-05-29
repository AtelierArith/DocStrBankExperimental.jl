```
WrappedFunction(f)
```

状態を持たず、パラメータを持たない関数をラップします。関数が `Chain` に追加されるときに使用されることがあります。例えば、`Chain(x -> relu.(x))` は機能しませんが、正しい方法は `Chain((x, ps, st) -> (relu.(x), st))` です。より簡単な方法は `Chain(WrappedFunction(Base.Fix1(broadcast, relu)))` です。

## 引数

  * `f`: いくつかの関数。

## 入力

  * `x`: `f` に直接渡されます。

## 戻り値

  * `f(x)` の出力
  * 空の `NamedTuple()`
