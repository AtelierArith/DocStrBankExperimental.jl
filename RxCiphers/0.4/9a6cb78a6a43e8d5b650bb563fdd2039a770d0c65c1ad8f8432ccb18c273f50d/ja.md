```
tokenise(txt::Txt, W::NCharSpace{1} = Alphabet) -> Vector{Int}, Dict{Int, String}
```

`txt`のトークンベクトルを返します。生のサブストリングはトークン（整数）としてエンコードされ、文字空間`W`のマッピングに従います。また、トークン化されないサブストリングの位置を格納する`frozen`辞書も返します。
