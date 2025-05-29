```
tokenise(txt::Txt, W::DLMSpace) -> Vector{Int}, Dict{Int, String}
```

`txt`のトークンベクトルを返します。生のサブストリングは、文字空間`W`のマッピングに従ってトークン（整数）としてエンコードされています。また、トークン化されないサブストリングの位置を格納する`frozen`辞書も返します。
