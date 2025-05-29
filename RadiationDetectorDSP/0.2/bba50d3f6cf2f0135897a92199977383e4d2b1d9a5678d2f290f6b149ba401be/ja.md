```
struct SamplingInfo{T<:RealQuantity,A<:AbstractVector{<:RealQuantity}}
```

サンプリング情報を保持します。

個々のサンプルの数値型は `T` で、（時間）軸は `axis` フィールドによって与えられます。

コンストラクタ:

  * `SamplingInfo{T,A}(axis)`
  * `SamplingInfo{T}(axis)`

フィールド:

  * `axis::AbstractVector{<:Union{Real, Unitful.AbstractQuantity{<:Real}}}`

```
