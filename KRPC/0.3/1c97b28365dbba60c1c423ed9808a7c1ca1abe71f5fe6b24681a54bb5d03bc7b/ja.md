```
generate_stubs(conn::KRPCConnection; save_file::Bool=false)
```

`conn`でサーバーが提供するスタブを生成（および`eval`）します。`save_file`が`true`の場合、スタブはパッケージのディレクトリに保存され、次回ラッパーがロードされるときにインポートされます。

ワールドエイジは、生成されたおよびevalされたスタブの使用を、最新のエイジにアクセスできるまで制限します。これは、REPLに戻るか、Base.invokelatestを使用するか、または別の`eval`呼び出しを通じて行われます。モノリシックなスクリプトを書く場合はこれを考慮してください - `generate_stubs`を呼び出す関数は、新しい定義にすぐにアクセスできません。

ワールドエイジに関する詳細は、https://docs.julialang.org/en/v1/manual/methods/#Redefining-Methods-1 のドキュメントや、https://arxiv.org/abs/2010.07516 のトピックに関する論文を参照してください。

# 例

```julia-repl
julia> generate_stubs(conn)
```
