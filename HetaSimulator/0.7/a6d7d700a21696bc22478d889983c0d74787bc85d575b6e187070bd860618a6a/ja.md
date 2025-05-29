```
load_platform(  
  target_dir::AbstractString;
  rm_out::Bool = true,
  source::String = "index.heta",
  type::String = "heta",
  kwargs...
)
```

HetaモデルをJuliaに変換し、`Platform`型を出力します。

詳細については`heta comiler`のドキュメントを参照してください: https://hetalang.github.io/#/heta-compiler/cli-references?id=running-build-with-cli-options

引数:

  * `target_dir` : Hetaプラットフォームディレクトリへのパス
  * `rm_out` : モデルがロードされた後にJuliaモデルのファイルを削除するべきか。デフォルトは`true`
  * kwargs : `heta_build`でサポートされている他の引数
