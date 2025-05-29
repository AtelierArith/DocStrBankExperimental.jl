```
transform!(st::Outliernicer, features::T) where {T<:Union{Vector,Matrix,DataFrame}}
```

IQRファクターに基づいて外れ値を特定し、DateValNNerを呼び出して最近傍の値で置き換えます。
