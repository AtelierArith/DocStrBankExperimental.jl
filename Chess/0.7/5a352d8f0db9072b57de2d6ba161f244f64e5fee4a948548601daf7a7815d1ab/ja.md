```
正方形
```

チェスボード上の正方形を表す型。

`Square`は、`Int`（a8=1、a7=2、...、a1=8、b8=9、b7=10、...、h1=64という規則）を使って構築することも、`SquareFile`と`SquareRank`を使って構築することもできます。また、ボード上のすべての64の正方形に対して、`SQ_A1`、...、`SQ_H8`という定数もあります。

# 例

```julia-repl
julia> Square(FILE_G, RANK_6)
SQ_G6

julia> Square(8)
SQ_A1
```
