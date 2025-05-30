```
complementary_mask(cache::BasicILMCache) -> GridData
complementary_mask(sys::ILMSystem) -> GridData
```

サーフェスの内部に0（すなわち法線ベクトルの反対側）を持ち、外部に1を持つグリッドデータを作成します。グリッドデータは`cache`の出力データ型と同じタイプです。`cache`は`GridScaling`のみを持つことが許可されています。キャッシュに浸漬されたサーフェスがない場合、すべての場所で0に戻ります。
