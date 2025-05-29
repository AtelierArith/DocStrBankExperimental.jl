```
read(stream::IO, [nb::Integer,] enc::Encoding)
read(filename::AbstractString, [nb::Integer,] enc::Encoding)
read(stream::IO, ::Type{String}, enc::Encoding)
read(filename::AbstractString, ::Type{String}, enc::Encoding)
```

文字エンコーディング `enc` でテキストを読み取るためのメソッド。詳細については、`enc` 引数なしの対応するメソッドのドキュメントを参照してください。
