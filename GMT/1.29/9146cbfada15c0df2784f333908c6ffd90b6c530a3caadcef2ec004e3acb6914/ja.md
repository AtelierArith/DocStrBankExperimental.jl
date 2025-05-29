```
gmtmath(cmd::String, args...)
```

すべてのコマンドを単一の文字列 'cmd' で gmtmath に呼び出します。これは gmt("gmtmath ....") と比較して自体としてはあまり役に立ちませんが、'movie' では非常に便利で、julia コマンドからシェルスクリプトを生成できます。

完全な GMT ( `GMT.jl` ではない) ドキュメントは [`grdmath`](http://docs.generic-mapping-tools.org/latest/grdmath.html) を参照してください。
