```
auc(::roc; pfa=1.0, pmiss=1.0, normalize=true)
```

曲線の下の面積を計算し、`auc → 0` はより良いパフォーマンスを示します。

オプションのパラメータ `pfa` または `pmiss` は、ROC曲線の一部のみを統合することを制限します。 `normalize` は部分ROCを自明なROCと比較することを示します。
