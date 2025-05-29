```
Cashflow(amount,time)
```

`Cahflow{A,B}` は `time` に `amount` を支払う契約です。

キャッシュフローは以下のようにできます：

  * 単項 `-` 演算子で否定できます。
  * 加算/減算できますが、`time` は `isapprox` 等しい必要があります。
  * スカラーで乗算/除算できます。

スーパタイプ階層 ≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡

```
Cashflow{A<:Real, B<:Timepoint} <: FinanceCore.AbstractContract <: Any
```
