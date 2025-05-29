```julia
@load "filename.jld"
@load "filename.jld" var1 [var2 var3 ...]
```

ファイル `filename.jld` に含まれる変数 `var1`、`var2` などを現在のグローバルスコープにロードします。

変数名が指定されていない場合、ファイル内のすべての変数がロードされます。

ロードされた変数の名前に対応する `Symbol` の `Vector` を返します。
