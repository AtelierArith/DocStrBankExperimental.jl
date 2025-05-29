```
randomprocess(N::Int64; kwargs...)

randomprocess(ElT::Type{<: Number}, N::Int64; kwargs...)
```

N量子ビットのランダム量子プロセスを生成します。

オプションで、`randomprocess(Float64, 10)`のように要素タイプを選択できます（デフォルトは複素数です）。

# 引数

  * `N`: 量子ビットの数
  * `mixed`: false（デフォルト）の場合、ランダムMPOを生成します。trueの場合、ランダムLPDOを生成します。
  * `alg`: 初期化基準、`"randompars"`に設定します（`randomstate`を参照）。
  * `σ`: `alg="rand"`における0中心の一様分布のサイズ。
  * `χ`: MPO/LPDOのボンド次元。
  * 'ξ`: クラウス次元（LPDO）。
