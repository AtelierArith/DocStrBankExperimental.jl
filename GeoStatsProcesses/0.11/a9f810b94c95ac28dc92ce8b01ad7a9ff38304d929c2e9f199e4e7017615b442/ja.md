```
QuiltingProcess(trainimg, tilesize; [options])
```

トレーニング画像 `trainimg` とタイルサイズ `tilesize` を使用した画像キルティングプロセスで、Hoffimann et al. 2017 に記載されています。

## オプション

  * `overlap`  - オーバーラップサイズ（デフォルトは (1/6, 1/6, ..., 1/6)）
  * `path`     - 処理パス（`:raster`（デフォルト）、`:dilation`、または `:random`）
  * `soft`     - ジオスペーシャルデータオブジェクトのペア `(data,dataTI)`（デフォルトは `nothing`）
  * `tol`      - 初期緩和許容値 (0,1]（デフォルトは `0.1`）

## 参考文献

  * Hoffimann et al 2017. [プロセスベースの地質モデルの画像キルティングによる確率的シミュレーション](https://www.sciencedirect.com/science/article/abs/pii/S0098300417301139)
  * Hoffimann et al 2015. [画像キルティングによる進化する風景の地質統計モデル化](https://www.researchgate.net/publication/295902985_Geostatistical_Modeling_of_Evolving_Landscapes_by_Means_of_Image_Quilting)
