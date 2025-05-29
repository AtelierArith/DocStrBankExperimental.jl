```
build_dependency_graph(
    info::Union{Pkg.API.ProjectInfo,Pkg.API.PackageInfo}=Pkg.project(),
    visited_packages::AbstractVector{String}=Vector{String}(),
)::Dict{String,Union{Dict,Nothing}}
```

現在アクティブなプロジェクトの依存関係グラフを構築します。

# 引数

  * `project_info::Union{Pkg.API.ProjectInfo,Pkg.API.PackageInfo}`: 現在のプロジェクトおよびJuliaパッケージに関するプロパティ、例えば名前やバージョン
  * `visited_packages::AbstractVector{String}`: すでに処理されたパッケージのリスト

# 戻り値

アクティブなプロジェクトの依存関係図を`Dict`に格納して返します。キーは常にパッケージ名です。値は、パッケージに依存関係がある場合は`Dict`、依存関係がない場合は`nothing`です。パッケージが複数回依存関係として現れる場合、最初の出現のみが依存関係を持ち、他の出現は依存関係を持ちません。標準ライブラリのパッケージは無視されます。
