```
readframetrcs!(io, trcs, hdrs, idx...)
```

JavaSeisデータセットから単一フレームをインプレースで読み込みます（トレースのみ）。完全なフレームでない場合、結果のトレースは左揃えになります。例：

# 3D:

```julia
io = jsopen("data_3D.js")
trcs = allocframetrcs(io)
frm_idx = 1
readframetrcs!(io, trcs, frm_idx)
```

# 4D:

```julia
io = jsopen("data_4D.js")
trcs = allocframetrcs(io)
frm_idx, vol_idx = 1, 1
readframetrcs!(io, trcs, frm_idx, vol_idx)
```

# 5D:

```julia
io = jsopen("data_5D.js")
trcs = allocframetrcs(io)
frm_idx, vol_idx, hyp_idx = 1, 1, 1
readframetrcs!(io, trcs, frm_idx, vol_idx, hyp_idx)
```
