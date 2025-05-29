```
applytoall!(gate::PauliRotation, theta, psum, aux_psum; kwargs...)
```

`PauliRotation`ゲートのための`applytoall!`のオーバーロードです。`apply()`関数の型不安定性を修正し、`psum`と`aux_psum`の間でパウリ文字列を移動するのを減らします。`psum`と`aux_psum`は後でマージされます。
