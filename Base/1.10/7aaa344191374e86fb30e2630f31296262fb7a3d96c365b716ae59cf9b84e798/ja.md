```
redirect_stdout([stream]) -> stream
```

すべてのCおよびJuliaレベルの[`stdout`](@ref)出力がリダイレクトされるパイプを作成します。パイプの端を表すストリームを返します。[`stdout`](@ref)に書き込まれたデータは、パイプの`rd`端から読み取ることができます。

!!! note
    `stream`は、`IOStream`、`TTY`、`Pipe`、ソケット、または`devnull`などの互換性のあるオブジェクトでなければなりません。


関連情報として[`redirect_stdio`](@ref)も参照してください。
