```julia
construct_interpolations(x, y; method, order, extrapolation)

```

N-D配列`y`の最後の次元に沿ったグリッド`x`での補間を構築します。`method`は補間アルゴリズムを指定し、"BSpline"または"Gridded"のいずれかです。`x`が`AbstractRange`の場合、デフォルトのメソッドは"BSpline"ですが、そうでない場合、デフォルトの`method`は"Gridded"です。`order`は補間の次数です。`x`が`AbstractRange`の場合、デフォルトの次数は2ですが、そうでない場合、デフォルトの次数は1です。`extrapolation`は外挿方法を指定し、任意の次元でその境界の外にある座標で補間オブジェクトにインデックスを付けようとした場合に何が起こるかを定義します。実装されている外挿方法は"line"、"flat"、または境界外評価のために返される"fill"値として使用される定数を渡すことができます。デフォルト値は0です。
