```
spelling(t::Union{CXType,CLType}) -> String
```

翻訳ユニットから来た言語のルールを使用して、基礎となる型をきれいに表示します。型が無効な場合、空の文字列が返されます。libclangの[`clang_getTypeSpelling`](@ref)のラッパーです。
