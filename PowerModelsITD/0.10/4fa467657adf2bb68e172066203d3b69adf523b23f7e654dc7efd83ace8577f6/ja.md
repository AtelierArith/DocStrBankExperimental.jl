```
function instantiate_model(
    pm_file::String,
    pmd_files::Vector,
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

電力伝送、電力配分、および境界リンク入力ファイル `pm_file`、`pmd_files` ベクター、および `pmitd_file` から PowerModelsITD モデリングオブジェクトをインスタンス化して返します。ここで、`pmitd_type` は統合電力伝送-配分モデリングタイプであり、`build_method` は考慮されている問題仕様のビルドメソッドです。`multinetwork` は、モデリングオブジェクトがマルチネットワークとして定義されるべきかどうかを定義するブール値です。`pmitd_ref_extensions` は電力伝送および配分モデリング拡張の配列です。`eng2math_passthrough` は PMD MATH モデルによって考慮されるパススルーベクターです。
