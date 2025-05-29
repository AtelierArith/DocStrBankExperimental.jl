readframehdrs(io, idx...)

JavaSeisデータセットから単一フレーム（ヘッダーのみ）をアウトオブプレースで読み取ります。完全なフレームでない場合、結果のヘッダーは左揃えになります。例：

# 3D:

```julia
frm_idx = 1
hdrs = readframehdrs(jsopen("data_3D.js"), frm_idx)
```

# 4D:

```julia
frm_idx, vol_idx = 1, 1
hdrs = readframehdrs(jsopen("data_4D.js"), frm_idx, vol_idx)
```

# 5D:

```julia
frm_idx, vol_idx, hyp_idx = 1, 1, 1
hdrs = readframehdrs(jsopen("data_5D.js"), frm_idx, vol_idx, hyp_idx)
```
