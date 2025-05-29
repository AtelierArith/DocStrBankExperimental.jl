```
applytoall!(gate::AmplitudeDampingNoise, theta, psum, aux_psum; kwargs...)
```

`AmplitudeDampingNoise`ゲートのための`applytoall!`のオーバーロードです。これは`apply()`関数の型不安定性を修正し、psumとaux*psumの間でパウリ文字列を移動させるのを減らします。`psum`と`aux*psum`は後でマージされます。
