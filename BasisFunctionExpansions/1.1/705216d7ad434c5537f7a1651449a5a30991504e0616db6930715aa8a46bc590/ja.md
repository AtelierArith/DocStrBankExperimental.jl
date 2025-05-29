```
LPVSS(x, u, nc; normalize=true, λ = 1e-3)
```

線形パラメータ変動状態空間モデル。変動係数行列 `x(t+1) = A(v)x(t) + B(v)u(t)` を持つ状態空間モデルを推定します。内部的には `X × U` の空間をスパンする `MultiRBFE` が使用されます。`x` と `u` は最初の次元に時間を持つ必要があります。中心は k-means を使用して自動的に見つけられます。詳細は `MultiRBFE` を参照してください。

# 例

```jldoctest
using Plots, BasisFunctionExpansions
x,xm,u,n,m = BasisFunctionExpansions.testdata(1000)
nc         = 10 # センターの数
model      = LPVSS(x, u, nc; normalize=true, λ = 1e-3) # モデルを推定
xh         = model(x,u) # 予測を形成

eRMS       = √(mean((xh[1:end-1,:]-x[2:end,:]).^2))

plot(xh[1:end-1,:], lab="予測", c=:red, layout=2)
plot!(x[2:end,:], lab="真の値", c=:blue); gui()
eRMS <= 0.37

# 出力

true
```
