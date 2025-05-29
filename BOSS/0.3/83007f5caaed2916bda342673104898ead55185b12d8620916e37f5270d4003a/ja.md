```
Domain(; kwargs...)
```

最適化ドメインを説明します。

# キーワード

  * `bounds::AbstractBounds`: `x`に対する基本的なボックス制約。このフィールドは必須です。
  * `discrete::AbstractVector{<:Bool}`: ドメインのいくつかの次元を離散的として指定するために使用できます。
  * `cons::Union{Nothing, Function}`: `x`に対する任意の非線形制約を定義するために使用されます。実行可能な点 `x` は `all(cons(x) .> 0.)` を満たさなければなりません。`cons` が提供されている場合、非線形制約を処理できる適切な獲得最大化器を使用する必要があります。(見てください [`AcquisitionMaximizer`](@ref).)
