```
splinevalue(spline::Spline, x[, ::Derivative{N}]; kwargs...)
```

`spline`の値、またはその`N`-次導関数を`x`で計算します。

パフォーマンスを向上させるために使用できる2つのオプションのキーワード引数があります：

  * `workspace`: デフォルトでは、関数は計算が行われる長さ`order(spline)`のベクトルを割り当てます。これを避けるために、`workspace`キーワードで事前に割り当てられたベクトルを提供できます。この場合、返される値は常に`eltype(workspace)`の型になります。
  * `leftknot`: 関連する区間のインデックス（すなわち、`intervalindex(basis(spline), x)`）が既に知られている場合、`leftknot`キーワードで提供できます。

`splinevalue`を呼び出す代わりに、スプラインオブジェクトを直接呼び出すことができます：`spline(x[, Derivative(N)]; kwargs...)`は`splinevalue(spline, x[, Derivative(N)]; kwargs...)`と同等です。

# 例

```jldoctest
julia> spl = Spline(BSplineBasis(4, 0:5), 1:8);

julia> splinevalue(spl, 1.7)
3.69775

julia> splinevalue(spl, 1.7, Derivative(1))
1.0225

julia> splinevalue(spl, 3.6, leftknot=7)
5.618

julia> spl(18//5)
2809//500

julia> spl(3.6, Derivative(3), leftknot=7)
0.5
```
