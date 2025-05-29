```julia
RossbyNumber(
    model;
    location,
    add_background,
    dWdy_bg,
    dVdz_bg,
    dUdz_bg,
    dWdx_bg,
    dUdy_bg,
    dVdx_bg
)

```

回転軸方向の渦度を使用してロスビー数を計算します。これは `model.coriolis` に従います。ロスビー数は次のように定義されます。

```
    Ro = ωᶻ / f
```

ここで、ωᶻはコリオリ回転軸の渦度であり、`f` はコリオリ回転周波数です。
