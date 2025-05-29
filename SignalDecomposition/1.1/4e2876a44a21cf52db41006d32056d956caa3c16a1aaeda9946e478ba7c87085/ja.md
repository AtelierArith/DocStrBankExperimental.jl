```
ExtremelySimpleNL(k::Int, ℓ::Int, w::Int, τ::Int, ε::Real) <: Decomposition
```

文字通り「非常に単純な非線形ノイズ除去法」[^Schreiber1993]です。これは`s`を**合計**`x + r`に分解し、`x`は「ノイズのない」時系列です。これは遅延埋め込み空間における隣接点の平均位置です。

この方法は、あなたの時系列が構造化された成分（決定論的かつ定常的な動力学に従い、埋め込みが近似すべきもの）といくつかのノイズの加算から構成されている場合にうまく機能します。

引用された論文には、最適な`ε`を選択するための情報があります。

引数:

  * `k` 過去の遅延の量
  * `ℓ` 前方の遅延の量
  * `w` タイラーウィンドウ
  * `τ` 遅延時間
  * `ε` 埋め込まれた空間における近傍の半径

[^Schreiber1993]: [Schreiber, (1993) Extremely simple nonlinear noise-reduction method. Physical Review E, 47(4)](https://doi.org/10.1103/PhysRevE.47.2401)
