```
iscrisp(a::AbstractAlgebra) = iscrisp(typeof(a))
```

代数がクリスプ（または*ブール*）であるのは、そのドメインが上限と下限の2つの値のみを持つときです。クリスプの対義語は*ファジー*です。

参照してください [`AbstractAlgebra`](@ref)。
