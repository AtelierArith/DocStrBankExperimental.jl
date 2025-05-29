```julia
sample_array(pt)

```

ターゲットチェーンのサンプルを、軸が `iteration x variable x target chain` の配列にコピーします。例えば、[`StabilizedPT`](@ref) では2つのターゲットチェーンがあります。デフォルトでは、生成されるチェーンは1つだけです。

変数がどのようにフラット化されるかについては、[`extract_sample()`](@ref) を参照し、フラット化された変数の文字列名を取得するには [`sample_names()`](@ref) を使用してください。

この関数と [`sample_names()`](@ref) の組み合わせは、[MCMCChains](https://turinglang.org/MCMCChains.jl/stable/getting-started/) を作成するのに便利で、これを使用して要約統計、診断、トレースプロット、ペアプロット（[PairPlots](https://sefffal.github.io/PairPlots.jl/dev/chains/) を介して）を取得できます。
