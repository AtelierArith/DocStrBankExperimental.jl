```
readframe!(io, trcs, hdrs, idx...)
```

JavaSeisデータセットからの単一フレームのインプレース読み込み。完全なフレームでない場合、結果のトレースとヘッダーは左揃えになります。例：

# 3D:

```julia
io = jsopen("data_3D.js")
trcs, hdrs = allocframe(io)
frm_idx = 1
readframe!(io, trcs, hdrs, frm_idx)
```

# 4D:

```julia
io = jsopen("data_4D.js")
trcs, hdrs = allocframe(io)
frm_idx, vol_idx = 1, 1
readframe!(io, trcs, hdrs, frm_idx, vol_idx)
```

# 5D:

```julia
io = jsopen("data_5D.js")
trcs, hdrs = allocframe(io)
frm_idx, vol_idx, hyp_idx = 1, 1, 1
readframe!(io, trcs, hdrs, frm_idx, vol_idx, hyp_idx)
```
