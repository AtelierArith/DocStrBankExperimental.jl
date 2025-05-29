```julia
drawTree(
    treel;
    show,
    suffix,
    filepath,
    xlabels,
    dpi,
    viewerapp,
    imgs
)

```

グラフviz `.dot` ファイルを用いてベイズ（ジャンクション）ツリーを描画します。Linux パッケージがインストールされていることを確認してください `sudo apt-get install graphviz xdot`。

ノート

  * `xlabels` はオプションで `cliqid=>xlabel` です。
