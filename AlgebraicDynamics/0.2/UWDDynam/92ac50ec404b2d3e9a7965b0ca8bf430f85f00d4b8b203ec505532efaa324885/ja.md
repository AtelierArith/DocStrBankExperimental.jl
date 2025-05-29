```
eval_dynamics(r::AbstractResourceSharer, u::AbstractVector, p, t)
```

リソースシェアラー `r` の状態 `u`、パラメータ `p` および時間 `t` におけるダイナミクスを評価します。`r` のダイナミクスがそれらに依存しない場合は、`p` と `t` を省略することができます。
