```
ArcMark(), AreaMark(), GroupMark(), ImageMark(), LineMark(), PathMark(), RectMark(), 
RuleMark(), ShapeMark(), SymbolMark(), TextMark(), TrailMark()
```

Create a mark of a specific type. [Vega docs](https://vega.github.io/vega/docs/marks/)

Arguments can be named arguments describing the mark structure. Pairs can be passed as  positional arguments to define channel encodings : `:x => scale(data.a)`. 

# Examples

```julia
sm = SymbolMark(shape="circle", 
    :xc            => xscale(dat.x), 
    :yc            => dat.y, 
    :stroke        => cscale(dat.a), 
)
```
