```
colorflow(flo; maxflow)
```

与えられたフローフィールド `flo` を視覚化し、方向を色で、長さを彩度でエンコードした画像を作成します（`maxflow` を使用してスケーリング）。欠損値は黒でエンコードされます。`maxflow` が省略された場合、入力から `maxflow` 関数を使用して計算されます。
