```
f64(x)
```

`x`の精度を`Float64`に変更します。これは、`Functors.fmap`を使用して構造体`x`のフィールドを再帰的にトラバースします。カスタム構造体（例：`<:BlochSimulator`や`<:AbstractTrajectory`）の場合、`typeof(x)`を`Functors.@functor`にする必要があります（例：`@functor FISP`）。

複雑なネストされたフィールドを持つ新しい構造体が導入された場合、新しい適応ルールを追加する必要があるかもしれません（`adapt_storage`に新しいメソッドを追加することによって）。
