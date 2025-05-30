```
CategoricalArray{T}(undef, dims::Dims; levels=nothing, ordered=false)
CategoricalArray{T}(undef, dims::Int...; levels=nothing, ordered=false)
```

レベルの型 `T <: Union{AbstractChar, AbstractString, Number}` と次元 `dims` を持つ初期化されていない `CategoricalArray` を構築します。

`levels` キーワード引数は、データの可能な値を指定するベクトルであることができます（これは、結果の配列に対して [`levels!`](@ref) を呼び出すよりも効率的です）。`ordered` キーワード引数は、配列の値がレベルの順序に従って比較できるかどうかを決定します（詳細は [`isordered`](@ref）を参照）。

```
CategoricalArray{T, N, R}(undef, dims::Dims; levels=nothing, ordered=false)
CategoricalArray{T, N, R}(undef, dims::Int...; levels=nothing, ordered=false)
```

上記の定義と似ていますが、デフォルトの型（`UInt32`）の代わりに参照型 `R` を使用します。

```
CategoricalArray(A::AbstractArray; levels=nothing, ordered=false)
```

`A` からの値と同じ要素型を持つ新しい `CategoricalArray` を構築します。

`levels` キーワード引数は、データの可能な値を指定するベクトルであることができます（これは、結果の配列に対して [`levels!`](@ref) を呼び出すよりも効率的です）。`levels` が省略され、要素型がそれをサポートしている場合、レベルは昇順にソートされます。そうでない場合、`A` における出現順序のまま保持されます。`ordered` キーワード引数は、配列の値がレベルの順序に従って比較できるかどうかを決定します（詳細は [`isordered`](@ref）を参照）。

もし `A` がすでに `CategoricalArray` である場合、そのレベル、順序性、および参照型は明示的に上書きされない限り保持されます。
