```
DSProblem{T, UT}(N::Int; poll::AbstractPoll=LTMADS{T}(),
                         search::AbstractSearch=NullSearch(),
                         objective::Union{Function,Nothing}=nothing,
                         initial_point::Vector=zeros(T, N),
                         iteration_limit::Int=1000,
                         function_evaluation_limit::Int=5000,
                         sense::ProblemSense=Min,
                         full_output::Bool=false,
                         granularity::Vector=zeros(T, N),
                         min_mesh_size::Union{T,Nothing}=nothing,
                         min_poll_size::Union{T,Nothing}=nothing,
                         kwargs...
                         ) where T
```

`N` 次元問題の定義を返します。型 `T` の数を使用します。

`poll` と `search` は使用するポールとサーチステップアルゴリズムを指定します。デフォルトの選択肢はそれぞれ [`LTMADS`](@ref) と [`NullSearch`](@ref) です。

問題には、すべての目的関数評価に渡されるユーザー定義のパラメータを含めることができます。これらのパラメータは、型 `UT` のフィールド内に保存されます。
