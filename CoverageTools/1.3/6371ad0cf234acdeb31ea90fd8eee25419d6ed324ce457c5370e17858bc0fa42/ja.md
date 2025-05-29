```
clean_folder(folder::AbstractString; include_memfiles::Bool=false)
```

指定されたディレクトリとサブディレクトリ内のすべての `.cov` およびオプションで `.mem` ファイルをクリーンアップします。 `process_folder` とは異なり、ルートフォルダのデフォルト値を含まないため、呼び出しコードはどのファイルが削除されるかをより明示的にする必要があります。
