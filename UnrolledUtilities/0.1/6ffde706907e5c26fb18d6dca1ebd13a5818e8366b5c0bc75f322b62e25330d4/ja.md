```
StaticBitVector{N, [U]}(f)
StaticBitVector{N, [U]}([bit])
```

`BitVector`の静的サイズの類似物で、型`U`の`Unsigned`チャンクを持ち、関数`f(n)`または定数`bit`を使用して構築できます。デフォルトでは、`U`は`UInt8`に設定され、`bit`は`false`に設定されています。

このイテレータは`Bool`のみを格納できるため、その`output_type_for_promotion`は`ConditionalOutputType`です。すべてのアンローリングされた関数に対して効率的な実装が提供されていますが、`unrolled_map`および`unrolled_accumulate`のメソッドは、出力の最初のアイテムが`Bool`である場合にのみ適用されます。
