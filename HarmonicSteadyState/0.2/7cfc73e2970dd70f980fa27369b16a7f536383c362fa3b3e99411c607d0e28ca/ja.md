```julia
get_single_solution(
    res::HarmonicSteadyState.Result{D, S, P, F} where F<:FunctionWrappers.FunctionWrapper{Array{S, 2}, Tuple{Array{S, 1}}};
    branch,
    index
)

```

`result`の`branch`の位置`index`におけるすべての変数とパラメータを指定する順序付き辞書を返します。
