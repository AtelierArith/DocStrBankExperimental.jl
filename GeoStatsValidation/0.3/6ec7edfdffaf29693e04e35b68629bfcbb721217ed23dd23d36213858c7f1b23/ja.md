```
KFoldValidation(k; shuffle=true, loss=Dict())
```

`k`-分割交差検証。オプションで、データを`shuffle`し、いくつかの変数に対して`LossFunctions.jl`からの`loss`関数を指定する辞書を指定します。

## 参考文献

  * Geisser, S. 1975. [予測サンプル再利用法とその応用](https://www.jstor.org/stable/2285815)
  * Burman, P. 1989. [通常の交差検証、v-分割交差検証、および繰り返し学習-テスト法の比較研究](https://www.jstor.org/stable/2336116)
