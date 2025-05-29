```
次元
```

すべての次元タイプの抽象スーパタイプです。

具体的な実装の例としては、[`X`](@ref)、[`Y`](@ref)、[`Z`](@ref)、[`Ti`](@ref)（時間）、およびカスタムの[`Dim`](@ref)次元があります。

`Dimension`は`AbstractDimArray`や他の次元オブジェクトの軸にラベルを付け、配列にインデックスを付けるために使用されます。

また、各配列軸のルックアップ値をラップすることもできます。これは配列軸の長さに一致する任意の`AbstractVector`である可能性がありますが、通常は構築されたオブジェクトで使用されるときに`Lookup`に変換されます。

`Lookup`は、次元に関する詳細を提供します。たとえば、それが[`Categorical`](@ref)であるか、[`Sampled`](@ref)であるか、あるいはあるトランセクトに沿った[`Points`](@ref)または[`Intervals`](@ref)であるかなどです。DimensionalDataは、渡されたインデックス値からルックアップを推測しようとします。

例:

```jldoctest Dimension
using DimensionalData, Dates

x = X(2:2:10)
y = Y(['a', 'b', 'c'])
ti = Ti(DateTime(2021, 1):Month(1):DateTime(2021, 12))

A = DimArray(zeros(3, 5, 12), (y, x, ti))

# 出力

╭────────────────────────────╮
│ 3×5×12 DimArray{Float64,3} │
├────────────────────────────┴─────────────────────────────────────────── dims ┐
  ↓ Y  Categorical{Char} ['a', 'b', 'c'] ForwardOrdered,
  → X  Sampled{Int64} 2:2:10 ForwardOrdered Regular Points,
  ↗ Ti Sampled{Dates.DateTime} Dates.DateTime("2021-01-01T00:00:00"):Dates.Month(1):Dates.DateTime("2021-12-01T00:00:00") ForwardOrdered Regular Points
└──────────────────────────────────────────────────────────────────────────────┘
[:, :, 1]
 ↓ →   2    4    6    8    10
  'a'  0.0  0.0  0.0  0.0   0.0
  'b'  0.0  0.0  0.0  0.0   0.0
  'c'  0.0  0.0  0.0  0.0   0.0
```

簡単のため、同じ`Dimension`タイプは`getindex`のラッパーとしても使用されます。例えば:

```jldoctest Dimension
x = A[X(2), Y(3)]

# 出力

╭────────────────────────────────╮
│ 12-element DimArray{Float64,1} │
├────────────────────────────────┴─────────────────────────────────────── dims ┐
  ↓ Ti Sampled{Dates.DateTime} Dates.DateTime("2021-01-01T00:00:00"):Dates.Month(1):Dates.DateTime("2021-12-01T00:00:00") ForwardOrdered Regular Points
└──────────────────────────────────────────────────────────────────────────────┘
 2021-01-01T00:00:00  0.0
 2021-02-01T00:00:00  0.0
 2021-03-01T00:00:00  0.0
 2021-04-01T00:00:00  0.0
 2021-05-01T00:00:00  0.0
 2021-06-01T00:00:00  0.0
 2021-07-01T00:00:00  0.0
 2021-08-01T00:00:00  0.0
 2021-09-01T00:00:00  0.0
 2021-10-01T00:00:00  0.0
 2021-11-01T00:00:00  0.0
 2021-12-01T00:00:00  0.0
```

`Dimension`は[`Selector`](@ref)をラップすることもできます。

```jldoctest Dimension
x = A[X(Between(3, 4)), Y(At('b'))]

# 出力

╭──────────────────────────╮
│ 1×12 DimArray{Float64,2} │
├──────────────────────────┴───────────────────────────────────────────── dims ┐
  ↓ X  Sampled{Int64} 4:2:4 ForwardOrdered Regular Points,
  → Ti Sampled{Dates.DateTime} Dates.DateTime("2021-01-01T00:00:00"):Dates.Month(1):Dates.DateTime("2021-12-01T00:00:00") ForwardOrdered Regular Points
└──────────────────────────────────────────────────────────────────────────────┘
 ↓ →   2021-01-01T00:00:00   2021-02-01T00:00:00  …   2021-12-01T00:00:00
 4    0.0                   0.0                      0.0
```
