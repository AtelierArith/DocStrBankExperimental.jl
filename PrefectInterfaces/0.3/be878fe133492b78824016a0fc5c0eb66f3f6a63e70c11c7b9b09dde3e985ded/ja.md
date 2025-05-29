PrefectInterfaces.jlは、以下を可能にする複合型を提供します：

  * PrefectサーバーへのインタラクティブなREPL接続。
  * パラメータを使用してPython APIから呼び出すことができるPrefectデプロイされたJuliaプロセス。

このパッケージを使用するには、環境変数`PREFECT_API_URL`で構成されたPrefectサーバーが実行中である必要があり、またはコンストラクタ呼び出しでエンドポイントURLを指定する必要があります。`PrefectBlock(blockname::String)`を呼び出すことで、名前によってPrefectブロック情報を取得できるため、これらのブロックによって定義されたリソースに接続するためのJuliaモジュールを構築できます。

# 例

```julia
julia> using PrefectInterfaces
julia> ENV["PREFECT_API_URL"] = "http://127.0.0.1:4300/api";

julia> ls()
5-element Vector{Any}:
 "aws-credentials/subdivisions"
 "docker-container/lamneth"
 "local-file-system/willowdata"
 "process/red-barchetta"
 "string/syrinx"

julia> dump(PrefectBlock("local-file-system/willowdata"))
PrefectBlock
  blockname: String "local-file-system/willowdata"
  block: LocalFSBlock
    blockname: String "local-file-system/willowdata"
    blocktype: String "local-file-system"
    basepath: String "/Users/mahiki/willowdata/dev"
    read_path: #4 (function of type PrefectInterfaces.var"#4#5"{String})
      basepath: String "/Users/mahiki/willowdata/dev"
```
