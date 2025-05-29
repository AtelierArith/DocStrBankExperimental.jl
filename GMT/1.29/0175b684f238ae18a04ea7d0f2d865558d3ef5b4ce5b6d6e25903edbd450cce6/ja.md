```
grdmath(cmd::String, args...)
```

すべてのコマンドを単一の文字列 'cmd' で grdmath に呼び出します。これは gmt("grdmath ....") を呼び出すことと比較して自体としてはあまり役に立ちませんが、'movie' では非常に便利で、julia コマンドからシェルスクリプトを生成できます。

完全な GMT ( `GMT.jl` ではない) ドキュメントは [`grdmath`](http://docs.generic-mapping-tools.org/latest/grdmath.html) を参照してください。
