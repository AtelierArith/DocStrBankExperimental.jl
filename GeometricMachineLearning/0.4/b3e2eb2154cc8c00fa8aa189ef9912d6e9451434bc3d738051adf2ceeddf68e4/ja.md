```
apply_section(λY::GlobalSection{T, AT}, Y₂::AT) where {T, AT <: StiefelManifold{T}}
```

`λY`を`Y₂`に適用します。

数学的には、これは要素$\lambda{}Y\in{}G$が同次空間$\mathcal{M}$の要素$Y_2$に対して行う群作用です。

内部的には[`apply_section!`](@ref)を呼び出します。
