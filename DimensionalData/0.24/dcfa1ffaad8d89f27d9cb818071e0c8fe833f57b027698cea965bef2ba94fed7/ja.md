```
set(x, val)
set(x, args::Pairs...) => x with updated field/s
set(x, args...; kw...) => x with updated field/s
set(x, args::Tuple{Vararg{Dimension}}; kw...) => x with updated field/s

set(dim::Dimension, index::AbstractArray) => Dimension
set(dim::Dimension, lookup::LookupArray) => Dimension
set(dim::Dimension, lookupcomponent::LookupArrayTrait) => Dimension
set(dim::Dimension, metadata::AbstractMetadata) => Dimension
```

オブジェクトのプロパティ、内部データ、またはその次元とルックアップインデックスの特性を設定します。

DimensionalDataは非常に強く型付けされているため、[`LookupArray`](@ref)のどのフィールドを`set`するかを指定する必要はありません - 曖昧さはありません。

`LookupArray`のフィールドを設定するには、次元を指定する必要があります。これは、`X => val`ペア、`X = val`キーワード引数、または`X(val)`でラップされた引数を使用して行うことができます。

`Dimension`または`LookupArray`が`set`に渡されて既存のものを置き換えると、設定されていないフィールドは元の値を保持します。

## 注意事項:

ルックアップインデックスの範囲/ベクトルを変更すると、適用可能な場合はステップサイズと順序も更新されます。

[`Order`](@ref)を`ForwardOrdered`のように設定しても、配列や次元を逆にして一致させることはありません。これを行うには、`reverse`と[`reorder`](@ref)を使用してください。

## 例

```jldoctest set
julia> using DimensionalData; const DD = DimensionalData
DimensionalData

julia> da = DimArray(zeros(3, 4), (custom=10.0:010.0:30.0, Z=-20:010.0:10.0));

julia> set(da, ones(3, 4))
3×4 DimArray{Float64,2} with dimensions:
  Dim{:custom} Sampled{Float64} 10.0:10.0:30.0 ForwardOrdered Regular Points,
  Z Sampled{Float64} -20.0:10.0:10.0 ForwardOrdered Regular Points
       -20.0  -10.0  0.0  10.0
 10.0    1.0    1.0  1.0   1.0
 20.0    1.0    1.0  1.0   1.0
 30.0    1.0    1.0  1.0   1.0 
```

`Dimension`ラッパータイプを変更します:

```jldoctest set
julia> set(da, :Z => Ti, :custom => Z)
3×4 DimArray{Float64,2} with dimensions:
  Z Sampled{Float64} 10.0:10.0:30.0 ForwardOrdered Regular Points,
  Ti Sampled{Float64} -20.0:10.0:10.0 ForwardOrdered Regular Points
       -20.0  -10.0  0.0  10.0
 10.0    0.0    0.0  0.0   0.0
 20.0    0.0    0.0  0.0   0.0
 30.0    0.0    0.0  0.0   0.0 
```

ルックアップ`Vector`を変更します:

```jldoctest set
julia> set(da, Z => [:a, :b, :c, :d], :custom => [4, 5, 6])
3×4 DimArray{Float64,2} with dimensions:
  Dim{:custom} Sampled{Int64} Int64[4, 5, 6] ForwardOrdered Regular Points,
  Z Sampled{Symbol} Symbol[:a, :b, :c, :d] ForwardOrdered Regular Points
     :a   :b   :c   :d
 4  0.0  0.0  0.0  0.0
 5  0.0  0.0  0.0  0.0
 6  0.0  0.0  0.0  0.0
```

`LookupArray`タイプを変更します:

```jldoctest set
julia> set(da, Z=DD.NoLookup(), custom=DD.Sampled())
3×4 DimArray{Float64,2} with dimensions:
  Dim{:custom} Sampled{Float64} 10.0:10.0:30.0 ForwardOrdered Regular Points,
  Z
 10.0  0.0  0.0  0.0  0.0
 20.0  0.0  0.0  0.0  0.0
 30.0  0.0  0.0  0.0  0.0
```

`Sampling`特性を変更します:

```jldoctest set
julia> set(da, :custom => DD.Irregular(10, 12), Z => DD.Regular(9.9))
3×4 DimArray{Float64,2} with dimensions:
  Dim{:custom} Sampled{Float64} 10.0:10.0:30.0 ForwardOrdered Irregular Points,
  Z Sampled{Float64} -20.0:10.0:10.0 ForwardOrdered Regular Points
       -20.0  -10.0  0.0  10.0
 10.0    0.0    0.0  0.0   0.0
 20.0    0.0    0.0  0.0   0.0
 30.0    0.0    0.0  0.0   0.0
```
