```
function instantiate_model(
    pmitd_data::Dict{String,<:Any},
    pmitd_type::Type,
    build_method::Function;
    multinetwork::Bool=false,
    pmitd_ref_extensions::Vector{<:Function}=Function[],
    eng2math_passthrough::Dict{String,Vector{String}}=Dict{String,Vector{String}}(),
    kwargs...
)
```

解析された電力送電および配電（PMITD）入力データ `pmitd_data` から PowerModelsITD モデリングオブジェクトをインスタンス化して返します。ここで、`pmitd_type` は統合された電力送電および配電モデリングタイプであり、`build_method` は考慮されている問題仕様のためのビルドメソッドです。`multinetwork` は、モデリングオブジェクトがマルチネットワークとして定義されるべきかどうかを定義するブール値です。`pmitd_ref_extensions` は電力送電および配電モデリング拡張の配列です。`eng2math_passthrough` は PMD MATH モデルによって考慮されるパススルーベクトルです。
