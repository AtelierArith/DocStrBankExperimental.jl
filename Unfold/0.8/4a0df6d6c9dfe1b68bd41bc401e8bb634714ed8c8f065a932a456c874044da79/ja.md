```
FileIO.save(file, uf::T; compress=false) where {T<:UnfoldModel}
```

UnfoldModelを（デフォルトでは圧縮されていない）.jld2ファイルに保存します。

メモリ効率のために、designmatrixはmissingに設定されています。必要に応じて、モデルをロードする際に再構築できます。
