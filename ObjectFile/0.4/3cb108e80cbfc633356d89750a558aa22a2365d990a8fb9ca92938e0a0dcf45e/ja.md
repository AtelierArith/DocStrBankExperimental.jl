```
readmeta(io::IO)
```

`IOStream` からオブジェクトファイルを読み取り、`ObjTypes` 内の各 `T` に対して `readmeta(io, T)` を呼び出すことでストリーム内のオブジェクトのタイプを推測し、`MagicMismatch` をスローしない最初のものを返します。
