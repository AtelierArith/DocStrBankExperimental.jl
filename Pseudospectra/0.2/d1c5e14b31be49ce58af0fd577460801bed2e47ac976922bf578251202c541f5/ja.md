```
driver!(ps_data, opts, gs=defaultgs(); revise_method=false)
```

擬似スペクトルを計算し、スペクトルポートレートをプロットします。

固有値と射影を取得するために反復法を使用する場合は、最初にそれを呼び出します。

# 引数

  * `ps_data::PSAStruct`: `new_matrix`によって処理された取り込まれた行列
  * `gs::GUIState`: グラフィカル出力を処理するオブジェクト
  * `opts::Dict{Symbol,Any}`:

      * `:ax`, 軸の制限（`ps_data`に保存された値を上書きします）。
      * `redrawcontour`、`arnoldiplotter!`に渡される他のオプション

`new_matrix()`によって`ps_data`に保存された多くのオプションが処理に影響を与えることに注意してください。

スペクトルポートレートを修正する際（`revise_method==true`）、`opts`内の以下のエントリも適用されます：

  * `:arpack_opts::ArpackOptions`,
  * `:direct::Bool`.
