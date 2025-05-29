```
evaluate!(c::Union{AbstractVector,Sequence}, a::Sequence, x)
```

`a`を`x`で評価します。結果は`c`に上書きされて保存されます。

関連情報: [`(::Sequence)(::Any, ::Vararg)`](@ref), [`evaluate`](@ref), [`Evaluation`](@ref), [`*(::Evaluation, ::Sequence)`](@ref) および [`(::Evaluation)(::Sequence)`](@ref).
