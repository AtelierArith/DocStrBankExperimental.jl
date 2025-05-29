```
on_before_update([callback,] model, trainer, out, grad)
```

`model`のパラメータを更新するために勾配`grad`を適用する`Optimisers.update!`の呼び出しの前に呼び出されます。`out`は、最後の[`train_step`](@ref)の呼び出しの出力です。
