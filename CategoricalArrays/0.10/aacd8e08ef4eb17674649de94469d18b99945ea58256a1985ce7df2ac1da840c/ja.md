```
CategoricalMatrix{T}(undef, m::Int, n::Int; levels=nothing, ordered=false)
```

初期化されていない `CategoricalMatrix` を、型 `T <: Union{AbstractChar, AbstractString, Number}` のレベルと次元 `dim` で構築します。`ordered` キーワード引数は、配列の値がレベルの順序に従って比較できるかどうかを決定します（[`isordered`](@ref) を参照）。

```
CategoricalMatrix{T, R}(undef, m::Int, n::Int; levels=nothing, ordered=false)
```

上記の定義に似ていますが、デフォルトの型（`UInt32`）の代わりに参照型 `R` を使用します。

```
CategoricalMatrix(A::AbstractMatrix; levels=nothing, ordered=false)
```

`A` から値を持ち、同じ要素型の `CategoricalMatrix` を構築します。

`levels` キーワード引数は、データの可能な値を指定するベクトルであることができます（これは、結果の配列に対して [`levels!`](@ref) を呼び出すよりも効率的です）。`levels` が省略され、要素型がそれをサポートしている場合、レベルは昇順にソートされます。そうでない場合、`A` に現れた順序が保持されます。`ordered` キーワード引数は、配列の値がレベルの順序に従って比較できるかどうかを決定します（[`isordered`](@ref) を参照）。

もし `A` がすでに `CategoricalMatrix` である場合、そのレベル、順序性、および参照型は明示的に上書きされない限り保持されます。
