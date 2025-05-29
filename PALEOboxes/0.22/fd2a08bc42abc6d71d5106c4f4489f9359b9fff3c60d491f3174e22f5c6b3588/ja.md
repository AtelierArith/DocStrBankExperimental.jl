```
value_ad(x::ADT) -> x
```

変数 `x` からスカラー値を取得します（AD導関数は破棄されます）。

これは、`x` を自動微分から除外し、したがってヤコビ行列の計算を行うために使用できます。例えば、`x` が小さな寄与であるが、ヤコビ行列をはるかに密にする場合です。

モデルコードは、使用される任意のADタイプに対してこれを実装する必要があります。例えば、

```
value_ad(x::SparsityTracing.ADval) = SparsityTracing.value(x)
value_ad(x::ForwardDiff.Dual) = ForwardDiff.value(x)
```
