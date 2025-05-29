```
dispersion(swt::SpinWaveTheory, qpts)
```

与えられた波ベクトルのリスト `qpts` は逆格子単位 (RLU) であり、各バンドの励起エネルギーを返します。戻り値 `ret` は2D配列であり、`ret[band_index, q_index]` のようにインデックス付けされるべきです。
