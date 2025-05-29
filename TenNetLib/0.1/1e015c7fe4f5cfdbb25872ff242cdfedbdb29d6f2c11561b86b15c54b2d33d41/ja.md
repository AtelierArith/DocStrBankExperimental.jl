```
function subspace_expand!(psi::TTN, node::Int2, nextnode::Int2,
                          max_expand_dim::Int, noise::Float64)
```

`node` と `nextnode` の間のボンド次元を `max_expand_dim` だけ拡大します。パラメータ `noise` は摂動の強さを制御します。
