```
applytoall!(gate::PauliNoise, p, psum, aux_psum; kwargs...)
```

ノイズ強度 `p` を持つ `PauliNoise` ゲートのための `applytoall!` のオーバーロードです。これは係数をインプレースで変更し、空のままの `aux_psum` を必要としません。
