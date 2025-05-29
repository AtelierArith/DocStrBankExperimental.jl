```
NGramMatrix{T, U, V} <: AbstractMatrix{U}
```

文字列のようなシーケンスを、計算の基数として `b` を使用し、モジュロとして `m` を使用して、基数 `n` の n-gram として遅延的に表現するための行列のような構造です。したがって、行列は `m` 行と各シーケンスを表すための1列を持ちます。欠落しているシーケンスもサポートされています。

参照: [`NGramIterator`](@ref), [`ngrams`](@ref), [`ngrams!`](@ref), [`countngrams`](@ref),     [`countngrams!`](@ref).
