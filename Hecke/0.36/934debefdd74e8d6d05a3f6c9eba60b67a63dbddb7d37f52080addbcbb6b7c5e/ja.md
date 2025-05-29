```
component(::Type{Field}, A::AbstractAssociativeAlgebra, i::Int)
  -> Vector{Tuple{Field, Morphism}}
```

与えられたエタール代数 $A$ とインデックス $i$ に対して、$A$ の $i$ 番目の単純成分を体 $K$ として返し、射影 $A \to K$ を返します。
