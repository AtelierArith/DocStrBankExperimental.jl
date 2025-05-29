```
read_observatories_mpc(s::String)
```

`s`内の`NEOs.OBSERVATORY_MPC_REGEX`の一致を`Vector{ObservatoryMPC{Float64}}`として返します。`s`はファイル名またはテキストのいずれかです。
