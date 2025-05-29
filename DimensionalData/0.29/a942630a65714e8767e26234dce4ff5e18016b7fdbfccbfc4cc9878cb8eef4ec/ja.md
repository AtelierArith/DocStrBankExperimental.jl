```
groupby(A::Union{AbstractDimArray,AbstractDimStack}, dims::Pair...)
groupby(A::Union{AbstractDimArray,AbstractDimStack}, dims::Dimension{<:Callable}...)
```

複数の次元にわたって、グループ化関数または[`Bins`](@ref)を使用して`A`をグループ化します。

## 引数

  * `A`: 任意の`AbstractDimArray`または`AbstractDimStack`。
  * `dims`: `groups = groupby(A, :dimname => groupingfunction)`のような`Pair`や、`groups = groupby(A, DimType(groupingfunction))`のようなラップされた[`Dimension`](@ref)です。グループ化関数の代わりに、グループビンを指定するために[`Bins`](@ref)を使用できます。

## 戻り値

[`DimGroupByArray`](@ref)が返されます。これは基本的に通常の`AbstractDimArray`ですが、グループ化された`AbstractDimArray`または`AbstractDimStack`を保持しています。その`dims`は、グループ化関数から返されたソートされた値を保持します。

基本的なJuliaおよびパッケージメソッドは、他の`AbstractArray`のように`DimGroupByArray`で動作します。

グループに対して`mean`や`sum`のような縮小関数をブロードキャストまたは`map`することが一般的です。例えば、`mean.(groups)`や`map(mean, groups)`のように。この操作は通常の`DimArray`を返しますが、縮小関数で`dims`キーワードが使用されている場合は`DimGroupByArray`を返し、そうでなければ`AbstractDimArray`または`AbstractDimStack`を返します。

# 例

時間次元に沿ってデータをグループ化します：

```jldoctest groupby; setup = :(using Random; Random.seed!(123))
julia> using DimensionalData, Dates

julia> A = rand(X(1:0.1:20), Y(1:20), Ti(DateTime(2000):Day(3):DateTime(2003)));

julia> groups = groupby(A, Ti => month) # 月ごとにグループ化
┌ 12-element DimGroupByArray{DimArray{Float64,3},1} ┐
├───────────────────────────────────────────────────┴───────────── dims ┐
  ↓ Ti Sampled{Int64} [1, 2, …, 11, 12] ForwardOrdered Irregular Points
├───────────────────────────────────────────────────────────── metadata ┤
  Dict{Symbol, Any} with 1 entry:
  :groupby => :Ti=>month
├─────────────────────────────────────────────────────────── group dims ┤
  ↓ X, → Y, ↗ Ti
└───────────────────────────────────────────────────────────────────────┘
  1  191×20×32 DimArray
  2  191×20×28 DimArray
  3  191×20×31 DimArray
  ⋮
 11  191×20×30 DimArray
 12  191×20×31 DimArray
```

そして平均を取ります：

```jldoctest groupby; setup = :(using Statistics)
julia> groupmeans = mean.(groups) # 月ごとの平均を取る
┌ 12-element DimArray{Float64, 1} ┐
├─────────────────────────────────┴─────────────────────────────── dims ┐
  ↓ Ti Sampled{Int64} [1, 2, …, 11, 12] ForwardOrdered Irregular Points
├───────────────────────────────────────────────────────────── metadata ┤
  Dict{Symbol, Any} with 1 entry:
  :groupby => :Ti=>month
└───────────────────────────────────────────────────────────────────────┘
  1  0.500064
  2  0.499762
  3  0.500083
  4  0.499985
  ⋮
 10  0.500874
 11  0.498704
 12  0.50047
```

月ごとの平均から日次の異常値を計算します。`-`ではなくブロードキャスト`.-`をマップすることに注意してください。これは、`mean`を適用した後に配列のサイズが一致しないためです。

```jldoctest groupby
julia> map(.-, groupby(A, Ti=>month), mean.(groupby(A, Ti=>month), dims=Ti));
```

またはYに対して別の操作を行います：

```jldoctest groupby
julia> groupmeans = mean.(groupby(A, Ti=>month, Y=>isodd))
┌ 12×2 DimArray{Float64, 2} ┐
├───────────────────────────┴────────────────────────────────────── dims ┐
  ↓ Ti Sampled{Int64} [1, 2, …, 11, 12] ForwardOrdered Irregular Points,
  → Y  Sampled{Bool} [false, true] ForwardOrdered Irregular Points
├────────────────────────────────────────────────────────────── metadata ┤
  Dict{Symbol, Any} with 1 entry:
  :groupby => (:Ti=>month, :Y=>isodd)
└────────────────────────────────────────────────────────────────────────┘
  ↓ →  false         true
  1        0.499594     0.500533
  2        0.498145     0.501379
  ⋮
 10        0.501105     0.500644
 11        0.498606     0.498801
 12        0.501643     0.499298
```
