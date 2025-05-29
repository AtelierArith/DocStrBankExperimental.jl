```
clean_file(filename::AbstractString; include_memfiles::Bool=false)
```

指定されたソースファイルに関連するすべての `.cov` およびオプションで `.mem` ファイルをクリーンアップします。これは、指定されたファイルのディレクトリ内のみを調べます。つまり、`.cov`/`.mem` ファイルはソースファイルの兄弟である必要があります。
