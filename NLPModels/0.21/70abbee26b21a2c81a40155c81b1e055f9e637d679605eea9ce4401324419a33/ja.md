```
f = obj(nls, x)
f = obj(nls, x, Fx; recompute::Bool=true)
```

`f(x)`を評価します。これは`nls::AbstractNLSModel`の目的関数です。`Fx`は残差`F(x)`の値で上書きされます。`recompute`が`true`の場合、`Fx`は`x`での残差で更新されます。
