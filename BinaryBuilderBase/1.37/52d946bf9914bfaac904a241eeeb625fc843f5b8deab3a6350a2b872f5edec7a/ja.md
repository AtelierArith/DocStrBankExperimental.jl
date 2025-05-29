```
setup_workspace(build_path::String, sources::Vector{SetupSource};
                verbose::Bool = false)
```

`build_path`内にワークスペースをセットアップし、さらなるステップに必要なディレクトリ構造を作成し、`build_path`内にソースを展開し、サンドボックス環境内で定義される環境変数を定義します。

このメソッドは、インストールするための`Prefix`と、このワークスペース内でコマンドを起動するために使用できるランナーを返します。
