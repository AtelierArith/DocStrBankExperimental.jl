```
seek(f::FLACDecoder, offset::Int64)
```

指定されたFLACストリーム内で絶対シークを実行します。要求されたシークが不可能な場合は`ArgumentError`をスローします。シークエラーが発生した場合は、デコーダーストリームを自動的に`flush()`します。
