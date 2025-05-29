```
data_rescale(x; old_range=[minimum(x), maximum(x)], new_range=[0, 1])
```

変数を新しい範囲に再スケーリングします。変数を0と1の間で正規化するために使用できます。

!!! danger
    この関数は現在内部で使用されており、別のパッケージに移動される可能性があります。直接使用することは避けてください。


# 引数

  * `x`: 再スケーリングするベクトル。
  * `old_range`: 再スケーリングするベクトルの古い範囲（デフォルトでは`x`の最小値と最大値から取得されます）。
  * `new_range`: `x`を再スケーリングする範囲。デフォルトでは、[0-1]。

# 例

```jldoctest
julia> data_rescale([1, 2, 3])
3-element Vector{Float64}:
 0.0
 0.5
 1.0

julia> data_rescale([1, 2, 3]; old_range=[1, 6], new_range=[1, 0])
3-element Vector{Float64}:
 1.0
 0.8
 0.6
```
