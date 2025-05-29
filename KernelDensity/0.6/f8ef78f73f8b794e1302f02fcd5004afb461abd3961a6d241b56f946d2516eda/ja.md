```
kde(data; kwargs...)
kde((xdata, ydata); kwargs...)
```

カーネル密度推定法。1Dまたは2D KDEオブジェクトを返します。使用されるグリッドと推定された密度の値は、それぞれフィールド`.x`と`.density`から取得できます。初期グリッドとは異なる点でkde値を取得するには、`pdf`メソッドを使用します。

キーワード引数は次のとおりです。

  * `boundary`: kdeの下限と上限、1Dの場合はタプル、2Dの場合はタプルのタプル、
  * `npoints`: 使用する補間点の数、
  * `kernel = Normal`: [Distributions.jl](https://github.com/JuliaStats/Distributions.jl)からの分布ファミリー、
  * `bandwidth`: カーネルのバンド幅; デフォルトはシルバーマンのルールを使用して計算されます。
