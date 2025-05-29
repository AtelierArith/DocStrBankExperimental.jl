```
jacobian_fd(semi::AbstractSemidiscretization;
            t0=zero(real(semi)),
            u0_ode=compute_coefficients(t0, semi))
```

セミ離散化 `semi` の右辺演算子と単純な二次有限差分を使用して、状態 `u0_ode` におけるセミ離散化 `semi` のヤコビ行列 `J` を計算します。
