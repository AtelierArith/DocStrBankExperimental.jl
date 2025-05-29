```
sort_terms!(a::MPoly{T}) where {T <: RingElement}
```

与えられた多項式の項を多項式環の順序に従ってソートします。ゼロ項および重複する指数は無視されます。それらに対処するには `combine_like_terms` を呼び出します。ソートされた多項式が返されます。
