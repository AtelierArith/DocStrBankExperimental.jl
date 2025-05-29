```
getARXregressor(y::AbstractVector,u::AbstractVecOrMat, na, nb; inputdelay = ones(Int, size(nb)))
```

短縮された出力信号 `y` と、最小二乗ARXモデルの次数 `na,nb` の推定値が `y\A` となる回帰行列 `A` を返します。

出力 `y` と入力 `u` を持つARXモデルをフィットさせるために使用される回帰行列を返します。形式は `A(z)y = B(z)u` であり、自己回帰の次数は `na`、入力移動平均の次数は `nb` であり、オプションの入力遅延 `inputdelay` があります。注意：入力遅延を変更すると次数が `nb + inputdelay - 1` に変わります。`inputdelay = 0` は直接項をもたらします。

# 例

```julia
A     = [1,2*0.7*1,1] # A(z) の係数
B     = [10,5] # B(z) の係数
u     = randn(100) # ガウス入力で100タイムステップをシミュレート
y     = filt(B,A,u)
yr,A  = getARXregressor(y,u,3,2) # システムの次数3,2を知っていると仮定
x     = A\yr # モデル多項式を推定
plot([yr A*x], lab=["信号" "予測"])
```

非線形ARXモデルについては、[BasisFunctionExpansions.jl](https://github.com/baggepinnen/BasisFunctionExpansions.jl/)を参照してください。また、`arx` も参照してください。
