```
CategoricalVector{T}(undef, m::Int; levels=nothing, ordered=false)
```

レベルの型 `T <: Union{AbstractChar, AbstractString, Number}` と次元 `dim` を持つ初期化されていない `CategoricalVector` を構築します。

`levels` キーワード引数は、データの可能な値を指定するベクトルであり（これは、結果の配列に対して [`levels!`](@ref) を呼び出すよりも効率的です）、`ordered` キーワード引数は、配列の値がレベルの順序に従って比較できるかどうかを決定します（詳細は [`isordered`](@ref）を参照）。

```
CategoricalVector{T, R}(undef, m::Int; levels=nothing, ordered=false)
```

上記の定義に似ていますが、デフォルトの型（`UInt32`）の代わりに参照型 `R` を使用します。

```
CategoricalVector(A::AbstractVector; levels=nothing, ordered=false)
```

`A` からの値と同じ要素型を持つ `CategoricalVector` を構築します。

`levels` キーワード引数は、データの可能な値を指定するベクトルであり（これは、結果の配列に対して [`levels!`](@ref) を呼び出すよりも効率的です）、`levels` が省略され、要素型がそれをサポートしている場合、レベルは昇順にソートされます。そうでない場合、レベルは `A` における出現順序のまま保持されます。`ordered` キーワード引数は、配列の値がレベルの順序に従って比較できるかどうかを決定します（詳細は [`isordered`](@ref）を参照）。

もし `A` がすでに `CategoricalVector` である場合、そのレベル、順序性、および参照型は明示的に上書きされない限り保持されます。
