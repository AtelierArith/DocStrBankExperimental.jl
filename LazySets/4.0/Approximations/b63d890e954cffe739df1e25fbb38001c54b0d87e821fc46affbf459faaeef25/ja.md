```
BoxDirections{N, VN} <: AbstractDirections{N, VN}
```

ボックス方向の表現。

### フィールド

  * `n` – 次元

### 注意事項

ボックス方向は、1つのエントリが±1で、他のすべてのエントリが0であるベクトルと見なすことができます。次元 $n$ では、そのような方向が $2n$ 存在します。

このテンプレートで使用されるデフォルトのベクトル表現は `ReachabilityBase.Arrays.SingleEntryVector` ですが、通常の `Vector` や `SparseVector` など、他の実装も使用できます。

### 例

テンプレートは次元を渡すことで構築できます。たとえば、次元が2の場合：

```jldoctest dirs_Box
julia> dirs = BoxDirections(2)
BoxDirections{Float64, ReachabilityBase.Arrays.SingleEntryVector{Float64}}(2)

julia> length(dirs)
4
```

デフォルトでは、各方向は `SingleEntryVector` として表現されます。つまり、1つの非ゼロ要素のみを持つベクトルです。

```jldoctest dirs_Box
julia> eltype(dirs)
ReachabilityBase.Arrays.SingleEntryVector{Float64}
```

2次元では、`BoxDirections` によって定義された方向はボックスの面に対して法線です。

```jldoctest dirs_Box
julia> collect(dirs)
4-element Vector{ReachabilityBase.Arrays.SingleEntryVector{Float64}}:
 [1.0, 0.0]
 [0.0, 1.0]
 [0.0, -1.0]
 [-1.0, 0.0]
```

数値型も指定できます：

```jldoctest
julia> dirs = BoxDirections{Rational{Int}}(10)
BoxDirections{Rational{Int64}, ReachabilityBase.Arrays.SingleEntryVector{Rational{Int64}}}(10)

julia> length(dirs)
20
```
