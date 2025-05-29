```
bsplines(basis, x[, derivative]; kwargs...)
```

`basis`のすべての非ゼロBスプラインの値および/または導関数を`x`で計算します。

`basis`のすべてのBスプラインが`x`でゼロの場合、`nothing`が返されます。`x`で非ゼロのBスプラインがある場合、`OffsetArray`が返されます。そのサイズと内容はオプションの`derivative`引数に依存します：

  * `derivative`が指定されていない場合、返される`OffsetArray`はインデックス`i`での`i`-th Bスプラインの値を含みます。
  * `derivative == Derivative(N)`の場合、返される`OffsetArray`はインデックス`i`での`i`-th Bスプラインの`N`-th導関数を含みます。
  * `derivative == AllDerivatives(N)`の場合、返される`OffsetArray`はインデックス`i, m`での`i`-th Bスプラインの`m`-th導関数（`0 ≤ m < N`）を含みます。

パフォーマンスを向上させるために使用できる2つのオプションのキーワード引数があります：

  * `derivspace`：導関数を計算する際、一部の係数はサイズ`(order(basis), order(basis))`の行列に格納されます。デフォルトでは、関数は新しい行列を割り当てます。これを避けるために、`derivspace`キーワードで事前に割り当てられた行列を提供できます。これは導関数を計算する際、すなわち`Derivative(N)`（`N ≥ 1`）または`AllDerivatives(N)`（`N ≥ 2`）でのみ使用できます。結果を含む配列も事前に割り当てるには、[`bsplines!`](@ref)関数を使用してください。
  * `leftknot`：関連する区間のインデックス（すなわち、`intervalindex(basis(spline), x)`）が既に知られている場合、`leftknot`キーワードで提供できます。

# 例

```jldoctest
julia> basis = BSplineBasis(4, 0:5);

julia> bsplines(basis, 2.4)
4-element OffsetArray(::Vector{Float64}, 3:6) with eltype Float64 with indices 3:6:
 0.03600000000000002
 0.5386666666666667
 0.41466666666666663
 0.01066666666666666

julia> bsplines(basis, 2.4, Derivative(1), derivspace=zeros(4,4))
4-element OffsetArray(::Vector{Float64}, 3:6) with eltype Float64 with indices 3:6:
 -0.18000000000000005
 -0.5599999999999999
  0.66
  0.07999999999999996

julia> bsplines(basis, 6) # returns nothing

julia> bsplines(basis, 17//5, leftknot=7)
4-element OffsetArray(::Vector{Rational{Int64}}, 4:7) with eltype Rational{Int64} with indices 4:7:
   9//250
 202//375
 307//750
   2//125

julia> bsplines(basis, 2.4, AllDerivatives(3))
4×3 OffsetArray(::Matrix{Float64}, 3:6, 0:2) with eltype Float64 with indices 3:6×0:2:
 0.036      -0.18   0.6
 0.538667   -0.56  -0.8
 0.414667    0.66  -0.2
 0.0106667   0.08   0.4
```
