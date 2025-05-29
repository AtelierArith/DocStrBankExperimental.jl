```
function instantiate_model(
    pm_file::String,
    pmd_file::String,
    pmitd_file::String,
    pmitd_type::Type,
    build_method::Function;
    multinetwork::Bool=false,
    pmitd_ref_extensions::Vector{<:Function}=Function[],
    eng2math_passthrough::Dict{String,Vector{String}}=Dict{String,Vector{String}}(),
    auto_rename::Bool=false,
    kwargs...
)
```

電力送電、電力配電、および境界リンク入力ファイル `pm_file`、`pmd_file`（1つのファイルが提供されます）、および `pmitd_file` から PowerModelsITD モデリングオブジェクトをインスタンス化して返します。ここで、`pmitd_type` は統合された電力送電-配電モデリングタイプであり、`build_method` は考慮されている問題仕様のビルドメソッドです。`multinetwork` は、モデリングオブジェクトがマルチネットワークとして定義されるべきかどうかを定義するブール値です。`pmitd_ref_extensions` は電力送電および配電モデリング拡張の配列です。`eng2math_passthrough` は PMD MATH モデルによって考慮されるパススルーベクトルです。
