```
LPVSS(x, u, v, nc; normalize=true, λ = 1e-3)
```

線形パラメータ変動状態空間モデル。変動係数行列を持つ状態空間モデルを推定します `x(t+1) = A(v)x(t) + B(v)u(t)`。内部的には、`v`の次元に応じて`MultiRBFE`または`UniformRBFE`が使用され、`v`の空間をスパンします。`x`、`u`、および`v`は最初の次元に時間を持つ必要があります。中心は自動的にk-meansを使用して見つけられます。詳細は`MultiRBFE`を参照してください。

# 例

```jldoctest
using Plots, BasisFunctionExpansions
T          = 1000
x,xm,u,n,m = BasisFunctionExpansions.testdata(T)
nc         = 4
v          = 1:T
model      = LPVSS(x, u, v, nc; normalize=true, λ = 1e-3)
xh         = model(x,u,v)

eRMS       = √(mean((xh[1:end-1,:]-x[2:end,:]).^2))

plot(xh[1:end-1,:], lab="予測", c=:red, layout=(2,1))
plot!(x[2:end,:], lab="真の値", c=:blue); gui()
eRMS <= 0.26

# 出力

true
```
