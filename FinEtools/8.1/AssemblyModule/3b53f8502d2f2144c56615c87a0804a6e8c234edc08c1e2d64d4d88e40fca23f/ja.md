```
expectedntriples(
    a::A,
    elem_mat_nrows::IT,
    elem_mat_ncols::IT,
    n_elem_mats::IT,
) where {A<:AbstractSysmatAssembler, IT}
```

アセンブラが格納することを期待するトリプル (I, J, V) の数はいくつですか？

デフォルトは：要素行列のサイズの積と行列の数の積です。
