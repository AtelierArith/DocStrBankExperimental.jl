```
Linear{T,R} <: AbstractLinear{T,R}

Linear{T,R}(itr)
```

イテレータ `itr` によって提供された項-係数ペアから、項の型 `T` と係数の型 `R` を持つ `Linear` 型の線形結合を構築します。

このタイプの線形結合は、項と（ゼロでない）係数が内部的に辞書に格納されているという意味でスパースです。

このコンストラクタの他の使い方については `AbstractLinear` の下で議論されています。

参照してください [`AbstractLinear`](@ref), [`DenseLinear`](@ref), [`Linear1`](@ref).
