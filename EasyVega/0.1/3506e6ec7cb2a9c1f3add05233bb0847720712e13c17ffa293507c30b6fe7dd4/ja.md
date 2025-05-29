```
ArcMark(), AreaMark(), GroupMark(), ImageMark(), LineMark(), PathMark(), RectMark(), 
RuleMark(), ShapeMark(), SymbolMark(), TextMark(), TrailMark()
```

特定のタイプのマークを作成します。[Vega docs](https://vega.github.io/vega/docs/marks/)

引数はマーク構造を説明する名前付き引数です。ペアはチャネルエンコーディングを定義するための位置引数として渡すことができます: `:x => scale(data.a)`。

# 例

```julia
sm = SymbolMark(shape="circle", 
    :xc            => xscale(dat.x), 
    :yc            => dat.y, 
    :stroke        => cscale(dat.a), 
)
```
