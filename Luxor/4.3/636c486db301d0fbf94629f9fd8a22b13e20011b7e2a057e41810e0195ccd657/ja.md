Luxorパッケージは、グラフィカルドキュメントを作成するためのベクタ描画関数のセットを提供します。

```julia
@draw begin
    circle(Point(0, 0), 100, :stroke)
    text("Hello World")
end
```
