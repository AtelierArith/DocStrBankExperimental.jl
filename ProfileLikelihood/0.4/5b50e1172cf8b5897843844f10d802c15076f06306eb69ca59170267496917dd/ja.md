```
mle(prob::LikelihoodProblem, alg, args...; kwargs...)
mle(prob::LikelihoodProblem, alg::Tuple, args...; kwargs...)
```

与えられた尤度問題 `prob` と最適化手法 `alg` に対して、MLEを見つけて [`LikelihoodSolution`](@ref) オブジェクトを返します。追加の引数やキーワード引数は `args...` と `kwargs...` を通じて渡すことができます。

`alg` が `Tuple` の場合、問題は各アルゴリズムの後に再最適化され、次の要素が `alg` から選ばれ、最初の推定値は前のアルゴリズムの解から得られます（最初は `get_initial_estimate(prob)` から始まります）。
