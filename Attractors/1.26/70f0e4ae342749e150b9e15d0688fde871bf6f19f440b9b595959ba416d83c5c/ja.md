```
basins_fractal_test(basins; ε = 20, Ntotal = 1000) -> test_res, Sbb
```

自動テストを実行して、Puy et al. の方法に基づいて、流域の境界がフラクタル構造を持っているかどうかを判断します [Puy2021](@cite)。`test_res`（`:fractal` または `:smooth`）と平均流域境界エントロピーを返します。

## キーワード引数

  * `ε = 20`: 流域境界エントロピーを計算するためのボックスのサイズ。
  * `Ntotal = 1000`: `Sbb` の計算のために境界でテストするボールの数。

## 説明

このテストは、サイズ `ε` の拡大鏡でランダムに流域を「見る」ことによって行われます。拡大鏡で見えるものが（平均的に）滑らかな境界のように見える場合、境界が滑らかであると判断します。滑らかでない場合、スケール `ε` で構造があると言えます。つまり、フラクタルです。

実際には、アルゴリズムは半径 `ε` の `Ntotal` 個のランダムボックスに対して境界流域エントロピー `Sbb` [`basin_entropy`](@ref) を計算します。計算された値が滑らかな境界の理論値（統計的誤差やバイアスを考慮）と等しい場合、滑らかな境界があると判断します。応答 `test_res` は選択したボールの半径 `ε` に依存する可能性があることに注意してください。サイズが大きくなると、滑らかな境界に対して構造が観察され、*異なる* 答えが得られることがあります。

出力 `test_res` は流域の性質を説明するシンボルであり、出力 `Sbb` はサンプリング法による境界流域エントロピーの推定値です。
