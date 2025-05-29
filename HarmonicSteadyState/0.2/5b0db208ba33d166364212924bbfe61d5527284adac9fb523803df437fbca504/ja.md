```julia
transform_solutions(
    res::HarmonicSteadyState.Result{D, S, ParType, F} where {ParType<:Number, F<:FunctionWrappers.FunctionWrapper{Array{S, 2}, Tuple{Array{S, 1}}}},
    func;
    branches,
    realify
) -> Vector

```

`Result`オブジェクトとSymbolics.jl式を表す文字列`f`を受け取ります。対応する解に対して評価された`f`の値を持つ配列を返します。追加の置換ルールは、`rules`に`("a" => val)`または`(a => val)`の形式で指定できます。
