```
applytoall!(gate::FrozenGate, thetas, psum, aux_psum; kwargs...)
```

`FrozenGate`のための`applytoall!`のオーバーロード。凍結されたパラメータを持つラップされた`FrozenGate.gate`の`applytoall!`にリダイレクトします。
