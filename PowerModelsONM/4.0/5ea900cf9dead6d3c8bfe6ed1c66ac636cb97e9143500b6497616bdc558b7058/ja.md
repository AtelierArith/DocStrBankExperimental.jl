```
optimize_dispatch!(
    args::Dict{String,<:Any};
    solver::Union{Missing,String}=missing
)::Dict{String,Any}
```

最適なディスパッチ問題をインプレースで解決します。これは、[`entrypoint`](@ref entrypoint)で使用するためのもので、[`optimize_dispatch`](@ref optimize_dispatch)を使用します。もしこれを[`optimize_switches!`](@ref optimize_switches!)を実行した後に最適化するために使用している場合、これはその結果から正しいスイッチ状態がすでに`args["network"]`に伝播されていることを前提としています。

`solver`（デフォルト: `"nlp_solver"`）は、`args["solvers"]`からOPF問題に使用するソルバーを指定します。
