`Scale(α::Number,A::AbstractOperator)`

省略記法コンストラクタ: 

`*(α::Number,A::AbstractOperator)` 

`AbstractOperator`を因子`α`でスケールします。

```julia
julia> A = FiniteDiff((10,2))
δx  ℝ^(10, 2) -> ℝ^(9, 2)

julia> S = Scale(10,A)
αδx  ℝ^(10, 2) -> ℝ^(9, 2)

julia> 10*A         #省略記法 
αℱc  ℝ^10 -> ℝ^10

```
