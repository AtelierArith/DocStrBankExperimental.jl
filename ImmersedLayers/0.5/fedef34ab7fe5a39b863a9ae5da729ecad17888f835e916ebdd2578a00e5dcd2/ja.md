```
mask(cache::BasicILMCache) -> GridData
mask(sys::ILMSystem) -> GridData
```

サーフェスの内側に1（すなわち、法線ベクトルの反対側）を持ち、外側に0を持つグリッドデータを作成します。グリッドデータは`sys`の出力データ型と同じタイプです。`sys`は`GridScaling`のみを持つことが許可されています。キャッシュに浸漬されたサーフェスがない場合、すべての場所で1に戻ります。
