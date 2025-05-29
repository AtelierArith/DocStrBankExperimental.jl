```
getARXregressor(y::AbstractVector,u::AbstractVecOrMat, na, nb)
```

短縮された出力信号 `y` と、最小二乗ARXモデルの次数 `na,nb` の推定が `y\A` となる回帰行列 `A` を返します。

出力 `y` と入力 `u` を持つ、自己回帰の次数が `na` で入力移動平均の次数が `nb` である形 `A(z)y = B(z)f(u)` に基づいてARXモデルをフィットさせるために使用される回帰行列を返します。

# 例

ここでは、関数 `f(u) = √(|u|)` を用いてモデルをテストします。

```julia
A     = [1,2*0.7*1,1] # A(z) の係数
B     = [10,5] # B(z) の係数
u     = randn(100) # ガウス入力で100タイムステップをシミュレート
y     = filt(B,A,sqrt.(abs.(u)))
yr,A  = getARXregressor(y,u,2,2) # システムの次数 2,2 を知っていると仮定します
bfe   = MultiUniformRBFE(A,[1,1,4,4,4], normalize=true)
bfa   = BasisFunctionApproximation(yr,A,bfe, 1e-3)
e_bfe = √(mean((yr - bfa(A)).^2))
plot([yr bfa(A)], lab=["信号" "予測"])
```

詳細についてはREADME (`?BasisFunctionExpansions`) を参照してください。
