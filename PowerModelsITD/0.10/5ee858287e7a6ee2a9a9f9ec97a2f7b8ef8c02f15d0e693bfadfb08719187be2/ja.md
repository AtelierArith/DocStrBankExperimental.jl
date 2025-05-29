```
function solve_model(
    pmitd_data::Dict{String,<:Any},
    pmitd_type::Type, optimizer,
    build_method::Function;
    multinetwork::Bool=false,
    solution_processors::Vector{<:Function}=Function[],
    pmitd_ref_extensions::Vector{<:Function}=Function[],
    eng2math_passthrough::Dict{String,Vector{String}}=Dict{String,Vector{String}}(),
    make_si::Bool=true,
    solution_model::String="eng",
    kwargs...
)
```

統合された送電（PowerModels）および配電（PowerModelsDistribution）モデリングオブジェクトを、電力統合送電-配電入力データ `pmitd_data` からインスタンス化し、解決します。ここで、`pmitd_type` は統合された電力送電-配電モデリングタイプ、`build_method` は考慮されている問題仕様のビルドメソッド、`multinetwork` はモデリングオブジェクトが `multinetwork` として定義されるかどうかを定義するブール値、`solution_processors` はモデル解決プロセッサのベクトル、`pmitd_ref_extensions` はモデリング拡張の配列、`make_si` は結果がSIまたはパーユニットで返されるかどうかを決定するブール値です。`eng2math_passthrough` はPMD MATHモデルによって考慮されるパススルーベクトルです。`solution_model` は解決策がどのモデル、ENGまたはMATHで提示されるかを決定する文字列です。結果の辞書を返します。
