```
convert(LLVMType, typ::Type; allow_boxed=true)
```

現在のコンテキストでJulia型`typ`をそのLLVM表現に変換します。`allow_boxed`引数は、ボックス型が許可されるかどうかを決定します。
