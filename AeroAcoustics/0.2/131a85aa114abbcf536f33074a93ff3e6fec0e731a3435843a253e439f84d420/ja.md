```
sourceintegration(x::Vector,env::Environment,limits::Vector{T}) where T
sourceintegration(x::Vector,env::Environment,limits::Vector{Vector{T}}) where T
sourceintegration(x::FreqArray,env::Environment,limits::Vector{T}) where T
sourceintegration(x::FreqArray,env::Environment,limits::Vector{Vector{T}}) where T
```

直交座標 `[xmin,xmax,ymin,ymax]` で与えられた `limits` から `x` のソース統合。

```
src1 = [-0.1,0.1,-0.1,0.1]
src2 = [-0.2,0.0,-0.1,0.1]
limits = [src1,src2]
srcint = sourceintegration(x,env,limits)
```

オプションでキーワード `int_thres` を指定してソース統合の閾値を設定できます。デフォルトは `Inf` に設定されており、統合領域内のすべての値を合計します。
