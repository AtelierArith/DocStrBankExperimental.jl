```
Model{Ny,Nx,Nc,T}
```

任意のモデル仕様の抽象スーパタイプ。

# 型パラメータ

  * `Ny::Int`: データベクトル `y` の長さ。
  * `Nx::Int`: *変数* パラメータの数。
  * `Nc::Int`: 線形係数の数。
  * `T <: Union{Float64, ComplexF64}` は `eltype(y)` と等しい。
