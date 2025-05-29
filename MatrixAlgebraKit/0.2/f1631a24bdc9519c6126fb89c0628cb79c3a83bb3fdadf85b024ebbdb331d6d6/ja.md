```
MatrixAlgebraKit.select_algorithm(f, A, alg::AbstractAlgorithm)
MatrixAlgebraKit.select_algorithm(f, A, alg::Symbol; kwargs...)
MatrixAlgebraKit.select_algorithm(f, A, alg::Type; kwargs...)
MatrixAlgebraKit.select_algorithm(f, A; kwargs...)
MatrixAlgebraKit.select_algorithm(f, A, (; kwargs...))
```

関数 `f` を型 `A` の入力に対して実装するために使用するアルゴリズムを決定します。

`alg` が `AbstractAlgorithm` のインスタンスである場合、そのまま返されます。

`alg` がアルゴリズムの `Symbol` または `Type` である場合、返り値は対応するアルゴリズムコンストラクタを呼び出すことによって得られます。キーワード引数 `kwargs` はこのコンストラクタに渡されます。

`alg` が指定されていない場合（または `nothing` の場合）、アルゴリズムは自動的に [`MatrixAlgebraKit.default_algorithm`](@ref) によって選択され、キーワード引数 `kwargs` はアルゴリズムコンストラクタに渡されます。最後に、キーワード引数が `NamedTuple` の形で第三の位置引数として渡されるときも同様の動作が得られます。
