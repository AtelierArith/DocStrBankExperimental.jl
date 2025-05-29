```
randompointarray(w, h, d; attempts=20)
```

現在の原点 (0/0) と `width` および `height` で定義された長方形内にランダムに配置されたポイントの配列を返します。 `d` は各ポイント間の最小距離を決定します。空のスペースを埋めるために関数がより一生懸命に試みるようにしたい場合は `attempts` を増やしてください。機能するサンプルを探すのに時間がかかりすぎる場合は減らしてください。

これはブリッドソンのポアソンディスクサンプリングアルゴリズムを使用しています: https://www.cs.ubc.ca/~rbridson/docs/bridson-siggraph07-poissondisk.pdf

## 例

```julia
for pt in randompointarray(BoundingBox(), 20)
    randomhue()
    circle(pt, 10, :fill)
end
```
