```
kl_mutual_information(x, y; k=5, bias_correction=true)
```

xとyの間の相互情報量の最近傍「KGS」推定を計算します。

xとyは2次元配列であり、各列は1つのデータポイントを表します。詳細については、次を参照してください。

"Estimating Mutual Information" Alexander Kraskov, Harald Stoegbauer, and Peter Grassberger Physical Review E https://arxiv.org/pdf/cond-mat/0305641.pdf

"Demystifying Fixed k-Nearest Neighbor Information Estimators" Weihao Gao, Sewoong Oh, Pramod Viswanath EEE International Symposium on Information Theory - Proceedings https://arxiv.org/pdf/1604.03006.pdf

キーワード引数: k=5: 最近傍の数 bias_correction=true: Gaoのバイアス補正を適用するフラグ
