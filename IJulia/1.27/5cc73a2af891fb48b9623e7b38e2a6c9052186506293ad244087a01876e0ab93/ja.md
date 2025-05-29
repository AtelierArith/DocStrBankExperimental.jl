```
notebook(; dir=homedir(), detached=false, port::Union{Nothing,Int}=nothing)
```

`notebook()` 関数は Jupyter ノートブックを起動し、オペレーティングシステムのコマンドラインで `jupyter notebook` を実行するのと同等です。Julia からノートブックを起動する利点は、Jupyter がどのようにインストールされたかによって、ユーザーが `jupyter` 実行可能ファイルの場所を知らない可能性があることです。

デフォルトでは、ノートブックサーバーはユーザーのホームディレクトリで起動されますが、この場所は `dir` キーワード引数に希望のパスを渡すことで変更できます。例えば、`notebook(dir=pwd())` を使用して現在のディレクトリを使用します。

デフォルトでは、`notebook()` は戻りません。中断するには ctrl-c を押すか、Julia を終了する必要があり、これにより Jupyter が停止します。したがって、Jupyter を実行している間は Julia ターミナルを開いたままにしておく必要があります。あるいは、`notebook(detached=true)` を実行すると、`jupyter notebook` がバックグラウンドで起動し、Julia を終了しても実行を続けます。（Jupyter を停止する唯一の方法は、オペレーティングシステムのプロセスマネージャでそれを強制終了することになります。）

オプションのキーワード `port` が `nothing` でない場合、指定されたポート番号でノートブックを開きます。

JupyterLab インスタンスを起動するには、[`IJulia.jupyterlab()`](@ref) を参照してください。
