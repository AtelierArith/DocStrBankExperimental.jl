```
EDF.File{T,I<:IO}
```

サンプルが型 `T` の値としてエンコードされた EDF ファイルを表す型で、EDF ファイルの場合は `Int16`、BDF ファイルの場合は (内部で定義された) `Int24` です。

# フィールド

  * `io::I`
  * `header::FileHeader`
  * `signals::Vector{Union{Signal{T},AnnotationsSignal}}`
