```julia
@save "filename.jld" var1 [var2 var3 ...]
@save compress=true "filename.jld" var1 [var2 var3 ...]
```

変数 `var1`（およびオプションで `var2`、`var3` など）を JLD ファイル "filename.jld" に保存します。オプションで、最初の引数として `compress=true` または `compress=false` を指定して、結果の `.jld` ファイルを圧縮するかどうかを指定できます（デフォルト=`false`）。
