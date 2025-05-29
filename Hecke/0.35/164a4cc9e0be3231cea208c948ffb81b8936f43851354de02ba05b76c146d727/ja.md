```
hermitian_space(E::NumField, gram::MatElem; cached::Bool = true) -> HermSpace
```

`E`上のエルミート空間を作成し、グラム行列は`gram`に等しい。行列`gram`は、`E`の非自明な自己同型に関して、正方行列かつエルミートでなければならない。数体`E`は二次拡大でなければならず、すなわち、$degree(E) == 2$が成り立たなければならない。
