```
encodefunctioncall(f::ABIFunction, inputs::Array) -> data
encodefunctioncall(io::IO, f::ABIFunction, inputs::Array)
encodefunctioncall(io::IOBuffer, f::ABIFunction, inputs::Array) -> data
```

関数への呼び出しをエンコードする
