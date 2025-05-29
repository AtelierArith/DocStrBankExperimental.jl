```
M = normalized_legendre_matrix(t,n; tmin=minimum(t),tmax=maximum(t))
```

`n` 次のレジェンドル係数を時間点 `t` で計算する行列を生成します。`t` はベクトルまたは範囲です。最も早い時間点と最新の時間点（最小値と最大値）は `t` の端から取得されます。これらの時間点 `tmin` と `tmax` をオプションとして提供することができます。

```juliadoctests
# 5から12までの3次までの係数
julia> M = normalized_legendre_matrix(5:12,3)

# 同じ式
julia> M = normalized_legendre_matrix([5,6,7,8,9,10,11,12],3)

# 上記と同様に時間点を1と15に設定
julia> M = normalized_legendre_matrix(5:12,3, tmin=1, tmax=15)
```
