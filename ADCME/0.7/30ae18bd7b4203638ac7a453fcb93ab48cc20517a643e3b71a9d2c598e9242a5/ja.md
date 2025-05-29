```
gradients(ys::PyObject, xs::PyObject; kwargs...)
```

`ys`に対する`xs`の勾配を計算します。

  * `ys`がスカラーの場合、`gradients`は`xs`と同じ形状の勾配を返します。
  * `ys`がベクトルの場合、`gradients`はヤコビアン$\frac{\partial y}{\partial x}$を返します。

!!! note
    2番目の使用法は推奨されません。なぜなら`ADCME`は逆モード自動微分を採用しているからです。`ys`がベクトルで`xs`がスカラーの場合、`gradients`は巧妙に前方モード自動微分を使用しますが、関連する演算子に対して2次の勾配が実装されている必要があります。

