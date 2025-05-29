```
bsplines!(dest, basis, x[, derivative]; kwargs...)
```

`x`における`basis`のすべての非ゼロBスプラインの値および/または導関数をインプレース（すなわち、`dest`内で）で計算します。

`basis`のすべてのBスプラインが`x`でゼロの場合、`nothing`が返されます。`x`で非ゼロのBスプラインがある場合、`dest`をラップした`OffsetArray`が返されます。そのサイズと内容はオプションの`derivative`引数に依存します：

  * `derivative`が指定されていない場合、返される`OffsetArray`はインデックス`i`での`i`-th Bスプラインの値を含みます。この場合、`dest`は長さ`order(basis)`のベクトルでなければなりません。
  * `derivative == Derivative(N)`の場合、返される`OffsetArray`はインデックス`i`での`i`-th Bスプラインの`N`-th導関数を含みます。この場合も、`dest`は長さ`order(basis)`のベクトルでなければなりません。
  * `derivative == AllDerivatives(N)`の場合、返される`OffsetArray`はインデックス`i, m`での`i`-th Bスプラインの`m`-th導関数（`0 ≤ m < N`）を含みます。この場合、`dest`はサイズ`(order(basis), N)`の行列でなければなりません。

パフォーマンスを向上させるために使用できる2つのオプションのキーワード引数があります：

  * `derivspace`：導関数を計算する際、一部の係数はサイズ`(order(basis), order(basis))`の行列に格納されます。デフォルトでは、関数は新しい行列を割り当てます。これを避けるために、`derivspace`キーワードで事前に割り当てられた行列を提供できます。これは導関数を計算する場合、すなわち`Derivative(N)`（`N ≥ 1`）または`AllDerivatives(N)`（`N ≥ 2`）でのみ使用できます。
  * `leftknot`：関連する区間のインデックス（すなわち、`intervalindex(basis(spline), x)`）がすでに知られている場合、`leftknot`キーワードで提供できます。

# 例

```jldoctest
julia> basis = BSplineBasis(4, 0:5);

julia> dest = zeros(4);

julia> bsplines!(dest, basis, 2.4)
4-element OffsetArray(::Vector{Float64}, 3:6) with eltype Float64 with indices 3:6:
 0.03600000000000002
 0.5386666666666667
 0.41466666666666663
 0.01066666666666666

julia> parent(ans) === dest
true

julia> bsplines!(dest, basis, -1.0) # returns nothing

julia> dest = zeros(4, 3);

julia> bsplines!(dest, basis, 3.75, AllDerivatives(3))
4×3 OffsetArray(::Matrix{Float64}, 4:7, 0:2) with eltype Float64 with indices 4:7×0:2:
 0.00260417  -0.03125    0.25
 0.315104    -0.65625    0.25
 0.576823     0.265625  -1.625
 0.105469     0.421875   1.125

julia> parent(ans) === dest
true
```
