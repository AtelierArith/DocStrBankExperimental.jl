```
readframehdrs!(io, hdrs, idx...)
```

JavaSeisデータセットから単一フレームをインプレースで読み取ります（ヘッダーのみ）。完全なフレームでない場合、結果のヘッダーは左揃えになります。例：

# 3D:

```julia
io = jsopen("data_3D.js")
hdrs = allocframehdrs(io)
frm_idx = 1
readframehdrs!(io, hdrs, frm_idx)
```

# 4D:

```julia
io = jsopen("data_4D.js")
hdrs = allocframehdrs(io)
frm_idx, vol_idx = 1, 1
readframehdrs!(io, hdrs, frm_idx, vol_idx)
```

# 5D:

```julia
io = jsopen("data_5D.js")
hdrs = allocframehdrs(io)
frm_idx, vol_idx, hyp_idx = 1, 1, 1
readframehdrs!(io, hdrs, frm_idx, vol_idx, hyp_idx)
```
