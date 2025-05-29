```
write_statistics_header(filename::String; guarded::Bool=false)
```

指定されたファイルに統計ログのヘッダーをクリアして書き込みます。ファイルが存在しない場合は、パスが存在する場合にのみ作成されます。guardedがtrueの場合、ファイルにすでにヘッダーが含まれているかどうかを事前にチェックし、以前の結果を上書きしないようにします。
