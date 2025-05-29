```
ElasticPDMat([m [, chol]]; capacity = 10^3, stepsize = 10^3)
```

弾性正定行列を初期 `capacity = 10^3` と `stepsize = 10^3` で作成します。オプションの引数 `m` は正定値対称行列であり、`chol` はそのコレスキー分解です。`append!` と `deleteat!` を使用して ElasticPDMat を変更します。
