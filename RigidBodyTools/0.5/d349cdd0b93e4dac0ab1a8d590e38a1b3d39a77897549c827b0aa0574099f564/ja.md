```
quaternion(θ::Real,v::SVector{3}) -> SVector{4}
```

与えられた回転角 `θ` と回転軸 `v` から四元数 $q = w + x\hat{i} + y\hat{j} + z\hat{k}$ を形成します。`v` は単位ベクトルである必要はありません。
