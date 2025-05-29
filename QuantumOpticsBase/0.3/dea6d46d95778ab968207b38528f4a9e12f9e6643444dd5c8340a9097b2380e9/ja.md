```
entanglement_entropy(state, partition, [entropy_fun=entropy_vn])
```

`state`とサイトのリスト`partition`およびシステムの残りの部分との間のエンタングルメントエントロピーを計算します。状態は複合基底で定義されている必要があります。

`state isa AbstractOperator`の場合、演算子空間のエンタングルメントエントロピーが計算され、次の性質を持ちます。

```julia
entanglement_entropy(dm(ket)) = 2 * entanglement_entropy(ket)
```

デフォルトでは、計算されたエントロピーはフォン・ノイマンエントロピーですが、異なる関数を提供することもできます（例えば、エンタングルメント・レーニーエントロピーを計算するために）。
