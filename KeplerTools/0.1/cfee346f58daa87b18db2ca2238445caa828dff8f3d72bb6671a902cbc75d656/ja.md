```
torb = p_lambert_velocity(sorbₛ, eorb, stime, etime, μ, s_patch_position=@SVector(zeros(3)), e_patch_position=@SVector(zeros(3)); kwargs...)
```

重力パラメータ `μ` を持つ天体の周りの単一周回軌道を計算し、時間 `stime` と `etime` における軌道 `sorb` と `eorb` の位置を通過します。

位置 `s_patch_position` と `e_patch_position` を提供することで、それぞれ開始位置と終了位置を変更できます。これは、影響範囲内のパッチングエラーを最小限に抑えるために使用できます。
