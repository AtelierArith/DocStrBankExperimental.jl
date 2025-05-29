```
solve_model(
    file::String,
    model_type::Type,
    optimizer::Any,
    build_method::Function;
    kwargs...)::Dict{String,<:Any}
```

入力ファイルからモデリングオブジェクトをインスタンス化し、解決します。ここで、`model_type`はモデルの定式化タイプ（例：NCWaterModel）、`optimizer`は問題を解決するために使用される最適化ソルバー（例：Gurobi.Optimizer）、`build_method`は考慮されている問題仕様を構築するために使用される関数（例：build*mn*owf）です。最適化結果の辞書を返します。
