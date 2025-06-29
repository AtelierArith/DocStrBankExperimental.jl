```
mju_boxQP(res, R, index, H, g, lower, upper)
```

最小化 0.5*x'*H*x + x'*g  s.t. lower <= x <= upper, 失敗した場合はランクまたは -1 を返す   入力:     n           - 問題の次元     H           - SPD 行列                n*n     g           - バイアスベクトル               n     lower       - 下限              n     upper       - 上限              n     res         - ソリューションのウォームスタート        n   戻り値:     nfree <= n  - 制約のない部分空間のランク、失敗した場合は -1   出力 (必須):     res         - ソリューション                  n     R           - 部分空間のコレスキー因子  nfree*nfree    割り当て: n*(n+7)   出力 (オプション):     index       - 自由次元のセット    nfree          割り当て: n   注意:     res の初期値はソルバーのウォームスタートに使用される     R は n*(n+7) のサイズが割り当てられている必要があるが、出力には nfree*nfree の値のみが使用される     index (指定されている場合) は n のサイズが割り当てられている必要があるが、出力には nfree の値のみが使用される     H と R の下三角のみがそれぞれ読み書きされる     便利な関数 mju_boxQPmalloc は必要なデータ構造を割り当てる

# 引数

  * **`res::Vector{Float64}`** -> 可変サイズのベクトル。`res` はベクトルである必要があり、行列ではありません。
  * **`R::Matrix{Float64}`** -> 可変サイズの行列。`R` のサイズは n*(n+7) である必要があります。
  * **`index::Vector{Int32}`** -> **オプション**の可変サイズのベクトル。`index` はベクトルである必要があり、行列ではありません。`index` のサイズは n と等しい必要があります。必要ない場合は `nothing` に設定できます。
  * **`H::Matrix{Float64}`** -> 可変サイズの行列。`H` は形状 (n, n) である必要があります。定数。
  * **`g::Vector{Float64}`** -> 可変サイズのベクトル。`g` はベクトルである必要があり、行列ではありません。`g` のサイズは n と等しい必要があります。定数。
  * **`lower::Vector{Float64}`** -> **オプション**の可変サイズのベクトル。`lower` はベクトルである必要があり、行列ではありません。`lower` のサイズは n と等しい必要があります。必要ない場合は `nothing` に設定できます。定数。
  * **`upper::Vector{Float64}`** -> **オプション**の可変サイズのベクトル。`upper` はベクトルである必要があり、行列ではありません。`upper` のサイズは n と等しい必要があります。必要ない場合は `nothing` に設定できます。定数。
