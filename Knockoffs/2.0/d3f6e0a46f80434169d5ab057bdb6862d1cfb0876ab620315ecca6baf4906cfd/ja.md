```
hmm_knockoff(snpdata::SnpData, r::AbstractVecOrMat, θ::AbstractMatrix, α::AbstractMatrix)
```

`snpdata`のノックオフを生成し、r、θ、αを読み込みます。

# 入力

  * `SnpData`: SnpArraysからの`SnpData`オブジェクト
  * `r`: fastPHASEによって推定されたrベクトル
  * `θ`: fastPHASEによって推定されたθ行列
  * `α`: fastPHASEによって推定されたα行列

# オプション入力

  * `outdir`: 生成されたノックオフの出力ディレクトリ
  * `plink_outfile`: ノックオフ遺伝子型の出力ファイル名
  * `estimate_δ`: trueの場合、尤度比境界を用いて各SNPのためのδ値を計算することで擬似FDRを推定します。
