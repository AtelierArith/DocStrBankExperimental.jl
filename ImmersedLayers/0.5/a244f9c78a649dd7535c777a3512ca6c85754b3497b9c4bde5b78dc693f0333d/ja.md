```
complementary_mask(cache::BasicILMCache) -> GridData
complementary_mask(sys::ILMSystem) -> GridData
```

サーフェスの内側に0（すなわち法線ベクトルの反対側）を持ち、外側に1を持つグリッドデータを作成します。グリッドデータは`cache`の出力データ型と同じタイプです。`cache`は`GridScaling`のみを持つことが許可されています。キャッシュに浸漬されたサーフェスがない場合、すべての場所で0に戻ります。
