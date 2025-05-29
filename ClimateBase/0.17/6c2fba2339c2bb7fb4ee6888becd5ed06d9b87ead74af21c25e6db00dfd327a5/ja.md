```
interpolation2pressure(A::ClimArray, P::ClimArray, plevels::Vector; kwargs...) → B
```

任意の高さ次元（高さ、モデルレベルなど）を持つ `A` を、垂直次元が圧力である新しい `B::ClimArray` に補間します。`P` は別の `ClimArray` で、パスカル単位の圧力値を持ち、その他は `A` と同じ空間時間構造を持っています。`plevels` 変数は、`B` が持つべき圧力レベルを示します。

キーワード `vertical_dim = Hei()` は、`A` のどの次元が「高さ」を示すかを指定します。キーワード `extrapolation_bc = Line()` は外挿を設定します。デフォルトでは線形ですが、`extrapolation_bc = NaN` のように任意の値を指定できます。他の外挿方法については、Interpolations.jl パッケージを使用してください。

キーワード `descending = true` は、圧力が垂直次元に沿って降順または昇順に並んでいるかどうかを指定します。
