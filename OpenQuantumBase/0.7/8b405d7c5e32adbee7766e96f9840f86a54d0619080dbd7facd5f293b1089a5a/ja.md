```julia
construct_interpolations(x, y; method, order, extrapolation)

```

N次元配列 `y` の最後の次元に沿った補間をグリッド `x` 上で構築します。`method` は補間アルゴリズムを指定し、"BSpline" または "Gridded" のいずれかです。`x` が `AbstractRange` の場合、デフォルトのメソッドは "BSpline" であり、それ以外の場合はデフォルトの `method` は "Gridded" です。`order` は補間の次数です。`x` が `AbstractRange` の場合、デフォルトの次数は 2 であり、それ以外の場合はデフォルトの次数は 1 です。`extrapolation` は外挿方法を指定し、任意の次元でその境界の外側の座標で補間オブジェクトにインデックスを付けようとした場合に何が起こるかを定義します。実装されている外挿方法は "line"、"flat"、または境界外評価のために返される "fill" 値として使用される定数を渡すことができます。デフォルト値は 0 です。
