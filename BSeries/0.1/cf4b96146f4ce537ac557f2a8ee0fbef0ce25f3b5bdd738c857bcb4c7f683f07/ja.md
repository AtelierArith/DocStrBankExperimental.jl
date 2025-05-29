```
bseries(csrk::ContinuousStageRungeKuttaMethod, order)
```

[`ContinuousStageRungeKuttaMethod`](@ref) `csrk` の B-series を、Miyatake & Butcher (2016) に記載された通り、指定された整数 `order` まで計算します。

!!! note "基本微分による正規化"
    このメソッドによって返される B-series の係数は、時間ステップのべき乗を `symmetry` で割り、入力ベクトル場 $f$ の対応する基本微分で掛ける必要があります。詳細は [`evaluate`](@ref) を参照してください。


# 例

[`AverageVectorFieldMethod`](@ref) は、単一のエントリが 1 のパラメータ行列によって与えられます。

```jldoctest
julia> M = fill(1//1, 1, 1)
1×1 Matrix{Rational{Int64}}:
 1

julia> series = bseries(ContinuousStageRungeKuttaMethod(M), 4)
TruncatedBSeries{RootedTree{Int64, Vector{Int64}}, Rational{Int64}} with 9 entries:
  RootedTree{Int64}: Int64[]      => 1
  RootedTree{Int64}: [1]          => 1
  RootedTree{Int64}: [1, 2]       => 1//2
  RootedTree{Int64}: [1, 2, 3]    => 1//4
  RootedTree{Int64}: [1, 2, 2]    => 1//3
  RootedTree{Int64}: [1, 2, 3, 4] => 1//8
  RootedTree{Int64}: [1, 2, 3, 3] => 1//6
  RootedTree{Int64}: [1, 2, 3, 2] => 1//6
  RootedTree{Int64}: [1, 2, 2, 2] => 1//4

julia> series - bseries(AverageVectorFieldMethod(), order(series))
TruncatedBSeries{RootedTree{Int64, Vector{Int64}}, Rational{Int64}} with 9 entries:
  RootedTree{Int64}: Int64[]      => 0
  RootedTree{Int64}: [1]          => 0
  RootedTree{Int64}: [1, 2]       => 0
  RootedTree{Int64}: [1, 2, 3]    => 0
  RootedTree{Int64}: [1, 2, 2]    => 0
  RootedTree{Int64}: [1, 2, 3, 4] => 0
  RootedTree{Int64}: [1, 2, 3, 3] => 0
  RootedTree{Int64}: [1, 2, 3, 2] => 0
  RootedTree{Int64}: [1, 2, 2, 2] => 0
```

# 参考文献

  * Yuto Miyatake and John C. Butcher. "エネルギー保存法の特性とハミルトン系のための並列積分器の構築." SIAM Journal on Numerical Analysis 54, no. 3 (2016): [DOI: 10.1137/15M1020861](https://doi.org/10.1137/15M1020861)
