```
record(
    cpm::CellPotts;
    file = "output.gif",
    steps = 300,
    framerate = 30,
    skip = 1,
    colorby = :type,
    kwargs...)
```

セルラー ポッツ モデルのアニメーションを生成します。

ファイル名を変更することでファイルタイプを変更します（例: `file = "output.mp4"`）。
