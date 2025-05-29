```
julialogo(;
    action=:fill,
    color=true,
    bodycolor=colorant"black",
    centered=false)
```

Juliaのロゴを描きます。デフォルトのアクションはロゴを塗りつぶし、色を使用します：

```
julialogo()
```

`color`が`false`の場合、ロゴには`bodycolor`の色が使用されます。

この関数は現在の描画状態（位置、スケールなど）を使用します。

`centered`キーワードを使用すると、ロゴを数学的中心に配置できますが、光学的中心は別の場所にあるかもしれません - 非対称デザインのため、うまく位置を決めるのは難しいです。

ロゴをクリッピングマスクとして使用するには：

```julia
julialogo(action=:clip)
```

（この場合、`color`設定は自動的に無視されます。）

ストローク（アウトライン）バージョンを取得するには：

```julia
julialogo(action=:path)
sethue("red")
strokepath()
```

TODO ブール値よりも有用なものを返す。
