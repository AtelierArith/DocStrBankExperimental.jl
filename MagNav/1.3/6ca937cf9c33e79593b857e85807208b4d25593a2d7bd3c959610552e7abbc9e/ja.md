```
plot_correlation_matrix(x::AbstractMatrix, features::Vector{Symbol};
                        dpi::Int         = 200,
                        Nmax::Int        = 1000,
                        show_plot::Bool  = true,
                        save_plot::Bool  = false,
                        plot_png::String = "correlation_matrix.png")
```

`2-5` の特徴の相関行列をプロットします。

**引数:**

  * `x`:         `N` x `Nf` データ行列（`Nf` は特徴の数）
  * `features`:  長さ `Nf` の特徴ベクトル（TL `A` などの成分を含む）
  * `dpi`:       （オプション）ドット毎インチ（画像解像度）
  * `Nmax`:      （オプション）プロットされるデータポイントの最大数
  * `show_plot`: （オプション）true の場合、`p1` を表示
  * `save_plot`: （オプション）true の場合、`p1` を `plot_png` として保存
  * `plot_png`:  （オプション）保存するプロットファイル名（`.png` 拡張子はオプション）

**戻り値:**

  * `p1`: 特徴間の相関行列のプロット
