```julia
makeCsmMovie(fg, tree; ...)
makeCsmMovie(
    fg,
    tree,
    cliqs;
    assignhist,
    show,
    filename,
    frames
)

```

`cliqs`のためのCSM状態遷移機械を割り当てて動画を作成する便利な関数です。

ノート

  * おそらくまだいくつかの初期の問題があります（優先度は低い）。
  * ソルバーパラメータが非同期だった場合、またはエラーが発生した場合は`assignhist`を使用してください。

関連

csmAnimate, printCliqHistorySummary
