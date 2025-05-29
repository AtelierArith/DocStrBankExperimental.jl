Newton CGソルバー。これはニュートンソルバーと同じですが、`H`がフルヘッセ行列である形式のシステムを解く代わりに、そのシステムを解くために行列フリー共役勾配アプローチを使用します。これは一般的に大規模なケースに対して好まれるべきです。

`optim_options`は[一般的な最適化オプション](https://julianlsolvers.github.io/Optim.jl/stable/#user/config/)です。`newtoncg_options`は[Krylov Trust Regionメソッドのオプション](https://github.com/JuliaNLSolvers/Optim.jl/blob/master/src/multivariate/solvers/second_order/krylov_trust_region.jl)です。

## 例

```julia
using MLJLinearModels, Optim

solver = MLJLinearModels.NewtonCG(
    optim_options = Optim.Options(time_limit = 20),
    newtoncg_options = (eta = 0.2,)
)
```
