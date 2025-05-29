```
InplaceBatchIntegralFunction(f!, prototype; max_batch::Integer=typemax(Int))
```

`f!(y, x, p)`の形のインプレースバッチ積分関数のコンストラクタで、配列`x`を受け入れ、評価点のバッチが配列の最後の軸に格納されます。`y`の結果と同じ型とサイズを持つ`prototype`配列が必要ですが、バッチ用に予約された最後の軸には少なくとも1つの要素が含まれている必要があります。`max_batch`キーワードは、同時にバッチ処理されるポイントの数に対するソフトリミットを設定します。
