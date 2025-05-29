```
prettypoly(points::Vector{Point}, vertexfunction = () -> circle(O, 2, :stroke);
    action=:none,
    close=false,
    reversepath=false,
    vertexlabels = (n, l) -> ()
    )
```

`points` で定義された多角形を描画し、現在のパラメータを使用して閉じたり逆転させたりし、次に多角形の各頂点で `vertexfunction` 関数を評価します。

デフォルトの `vertexfunction` は半径 2 の円を描画します。

多角形の各頂点にランダムに色付けされた塗りつぶし円をマークするには：

```julia
p = star(O, 70, 7, 0.6, 0, vertices=true)
prettypoly(p, action=:fill, () ->
    begin
        randomhue()
        circle(O, 10, :fill)
    end,
    close=true)
```

オプションのキーワード引数 `vertexlabels` を使用すると、現在の頂点番号と各頂点の総数にアクセスできる2つの引数を持つ関数を提供できます。たとえば、三角形の頂点に「1 of 3」、「2 of 3」、「3 of 3」とラベルを付けるには、次のようにします：

```julia
prettypoly(triangle, action=:stroke,
    vertexlabels = (n, l) -> (text(string(n, " of ", l))))
```
