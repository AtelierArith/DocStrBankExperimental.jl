```
randomstate(N::Int64; kwargs...)

randomstate(ElT::Type{<: Number}, N::Int64; kwargs...)
```

N量子ビットのランダム量子状態を生成します。

オプションで、要素タイプを指定できます。例えば、`randomstate(Float64, 10)`はランダムな実状態を生成します（デフォルトは複素数です）。

# 引数

  * `N`: 量子ビットの数
  * `mixed`: false（デフォルト）の場合、ランダムMPSを生成します。trueの場合、ランダムLPDOを生成します。
  * `alg`: 初期化に使用されるアルゴリズム：`"rand"`はランダムテンソル要素を初期化します；`"circuit"`はランダム量子回路で初期化します（MPSのみ）。
  * `σ`: `alg="rand"`の0中心の一様分布のサイズ。
  * `χ`: MPS/LPDOのボンド次元
  * 'ξ`: クラウス次元（LPDO）
  * `normalize`: trueの場合、正規化された状態を返します。
