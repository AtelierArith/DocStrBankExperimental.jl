```
vectorize(tc::MicroTC, text; bow=BOW(), textconfig=tc.textconfig, normalize=true)
vectorize(tc::MicroTC, bow::BOW; normalize=true)
```

モデルを使用して重み付けされたベクトルを作成します。入力の `text` は文字列または文字列の配列であり、すでに計算された単語の袋であることもできます。
