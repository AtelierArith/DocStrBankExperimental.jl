```
fits_read_keyword(f::FITSFile, keyname::String) -> (value, comment)
```

は、指定されたキーワードの値とコメントを（文字列のタプルとして）返し、キーワードが見つからない場合はエラーをスローします。
