```
linear_structure(semi::AbstractSemidiscretization;
                 t0=zero(real(semi)))
```

セミ離散化 `semi` の右辺演算子を、線形演算子 `A` とベクトル `b` によって与えられるアフィン線形演算子として、時刻 `t0` でラップします。
