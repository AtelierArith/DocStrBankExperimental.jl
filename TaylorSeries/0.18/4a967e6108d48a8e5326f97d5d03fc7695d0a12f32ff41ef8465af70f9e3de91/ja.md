```
`differentiate(a::TaylorN{T}, ntup::NTuple{N,Int})` 

`a` に対して、`ntup::NTuple{N,Int}` で定義された偏導関数を持つ `TaylorN` を返します。最初のエントリは最初の変数に関する導関数の数、2 番目は 2 番目の変数に関する導関数の数、以下同様です。
```
