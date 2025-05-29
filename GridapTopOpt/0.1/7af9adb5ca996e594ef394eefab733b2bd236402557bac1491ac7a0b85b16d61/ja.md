```
write_history(path::String,h::OptimiserHistory;ranks=nothing)
```

`OptimiserHistory`オブジェクトの内容を`path`に書き込みます。並列で実行する際はMPI `ranks`を指定してください。
