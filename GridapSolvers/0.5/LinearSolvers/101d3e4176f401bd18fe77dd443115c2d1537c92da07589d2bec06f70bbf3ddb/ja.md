```
struct RichardsonSmoother{A} <: LinearSolver
  M     :: A
  niter :: Int64
  ω     :: Float64
end
```

反復リチャードソンスムーザー。解 `x` と残差 `r` が与えられたとき、線形ソルバー `M` を使用して、減衰パラメータ `ω` で `niter` 回のリチャードソン反復を実行します。リチャードソン反復は次のように与えられます：

```
dx = ω * inv(M) * r
x  = x + dx
r  = r - A * dx
```

解 `x` と残差 `r` の両方をその場で更新します。
