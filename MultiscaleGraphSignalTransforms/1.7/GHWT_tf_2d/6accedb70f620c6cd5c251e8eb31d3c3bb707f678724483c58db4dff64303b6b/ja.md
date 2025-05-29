```
Bbasis, infovec = ghwt_tf_bestbasis_2d(dmatrix::Matrix{Float64},GProws::GraphPart,GPcols::GraphPart)
```

2次元時間周波数適応GHWT法の実装。Maj LindbergとLars F. Villemoesによる論文「適応Haar-Walshタイルを用いた画像圧縮」のアイデアを修正したものです。

### 入力引数

  * `dmatrix`: すべてのレベルで連結された2次元行列のghwt拡張係数。
  * `GProws`: 行に対応する親和行列。
  * `GPcols`: 列に対応する親和行列。

### 出力引数

  * `Bbasis`: ベストバasisの係数。
  * `infovec`: [infovec[i,1],infovec[i,2]]は、dmatrix内のBbasis[i]の位置です。

著作権 2018 カリフォルニア大学のレジデンツ

実装者: Yiqun Shao (アドバイザー: Dr. Naoki Saito)
