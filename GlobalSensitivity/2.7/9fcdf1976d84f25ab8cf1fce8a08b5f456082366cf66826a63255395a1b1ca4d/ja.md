```
Sobol(; order = [0, 1], nboot = 1, conf_level = 0.95)
```

  * `order`: 計算するインデックスの順序。デフォルトは [0,1] で、これはトータルおよびファーストオーダーインデックスを意味します。2を渡すと、セカンドオーダーインデックスの計算も可能になります。
  * `nboot`: 信頼区間の計算のために、`nboot` はブートストラップ実行の数 (>0) を指定する必要があります。
  * `conf_level`: 信頼レベルで、デフォルトは 0.95 です。

## メソッドの詳細

Sobol は分散ベースの手法であり、モデルまたはシステムの出力の分散を、入力または入力のセットに帰属できる部分に分解します。これにより、個々のパラメータの感度だけでなく、パラメータ間の相互作用からの影響と感度を定量化する方法も得られます。

$$
 Y = f_0+ \sum_{i=1}^d f_i(X_i)+ \sum_{i < j}^d f_{ij}(X_i,X_j) ... + f_{1,2...d}(X_1,X_2,..X_d)
$$

$$
 Var(Y) = \sum_{i=1}^d V_i + \sum_{i < j}^d V_{ij} + ... + V_{1,2...,d}
$$

Sobol インデックスは「順序」付けされており、ファーストオーダーインデックスは $S_i = \frac{V_i}{Var(Y)}$ であり、$X_i$ の主効果による出力分散への寄与を示します。したがって、これは他の入力パラメータの変動を平均化しながら、$X_i$ のみを変化させた場合の効果を測定します。これは、全体の分散によって標準化され、分数寄与を提供します。高次の相互作用インデックス $S_{i,j}, S_{i,j,k}$ などは、分散分解の他の項を $Var(Y)$ で割ることによって形成できます。

## API

```
gsa(f, method::Sobol, p_range::AbstractVector; samples, kwargs...)
gsa(f, method::Sobol, A::AbstractMatrix{TA}, B::AbstractMatrix;
         batch = false, Ei_estimator = :Jansen1999,
         distributed::Val{SHARED_ARRAY} = Val(false),
         kwargs...) where {TA, SHARED_ARRAY}
```

`Ei_estimator` は `:Homma1996`, `:Sobol2007` および `:Jansen1999` を取ることができ、これにより `Ei` 項のモンテカルロ推定器が使用されます。デフォルトは `:Jansen1999` です。これらの詳細は、対応する論文に記載されています：

  * `:Homma1996` - [Homma, T. and Saltelli, A., 1996. Importance measures in global sensitivity analysis of nonlinear models. Reliability Engineering & System Safety, 52(1), pp.1-17.](https://www.sciencedirect.com/science/article/abs/pii/0951832096000026)
  * `:Sobol2007` - [I.M. Sobol, S. Tarantola, D. Gatelli, S.S. Kucherenko and W. Mauntz, 2007, Estimating the approx- imation errors when fixing unessential factors in global sensitivity analysis, Reliability Engineering and System Safety, 92, 957–960.](https://www.sciencedirect.com/science/article/abs/pii/S0951832006001499) および [A. Saltelli, P. Annoni, I. Azzini, F. Campolongo, M. Ratto and S. Tarantola, 2010, Variance based sensitivity analysis of model output. Design and estimator for the total sensitivity index, Computer Physics Communications 181, 259–270.](https://www.sciencedirect.com/science/article/abs/pii/S0010465509003087)
  * `:Jansen1999` - [M.J.W. Jansen, 1999, Analysis of variance designs for model output, Computer Physics Communi- cation, 117, 35–43.](https://www.sciencedirect.com/science/article/abs/pii/S0010465598001544)
  * `:Janon2014` - [Janon, A., Klein, T., Lagnoux, A., Nodet, M., & Prieur, C. (2014). Asymptotic normality and efficiency of two Sobol index estimators. ESAIM: Probability and Statistics, 18, 342-364.](https://arxiv.org/abs/1303.6451)

### 例

```julia
using GlobalSensitivity, QuasiMonteCarlo

function ishi(X)
    A= 7
    B= 0.1
    sin(X[1]) + A*sin(X[2])^2+ B*X[3]^4 *sin(X[1])
end

samples = 600000
lb = -ones(4)*π
ub = ones(4)*π
sampler = SobolSample()
A,B = QuasiMonteCarlo.generate_design_matrices(samples,lb,ub,sampler)

res1 = gsa(ishi,Sobol(order=[0,1,2]),A,B)

function ishi_batch(X)
    A= 7
    B= 0.1
    @. sin(X[1,:]) + A*sin(X[2,:])^2+ B*X[3,:]^4 *sin(X[1,:])
end

res2 = gsa(ishi_batch,Sobol(),A,B,batch=true)
```
