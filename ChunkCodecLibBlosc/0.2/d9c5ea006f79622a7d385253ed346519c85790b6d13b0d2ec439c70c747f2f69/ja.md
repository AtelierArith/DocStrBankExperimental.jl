```
compcode(s::AbstractString)
```

Bloscによって内部的に圧縮器を識別するために使用される非負整数コードを返します。`s`がサポートされているアルゴリズムの名前でない場合、`ArgumentError`をスローします。
