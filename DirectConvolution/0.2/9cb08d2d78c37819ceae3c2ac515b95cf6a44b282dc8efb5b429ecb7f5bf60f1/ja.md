```
function SG_Filter(T::DataType=Float64;halfWidth::Int=5,degree::Int=2)
```

`SG_Filter`構造体を作成し、Savitzky-Golayフィルタを格納します。

  * フィルタの長さは2*`halfWidth`+1です
  * 多項式の次数は`degree`で、`maxDerivativeOrder`を定義します

これらのフィルタは次の関数を使用して適用できます。

  * `apply_SG_filter`
  * `apply_SG_filter2D`

例:

```jldoctest
julia> sg = SG_Filter(halfWidth=5,degree=3);


julia> maxDerivativeOrder(sg)
3

julia> length(sg)
11

julia> filter(sg,derivativeOrder=2)
Filter(r=-5:5,c=[0.03497, 0.01399, -0.002331, -0.01399, -0.02098, -0.02331, -0.02098, -0.01399, -0.002331, 0.01399, 0.03497])

```
