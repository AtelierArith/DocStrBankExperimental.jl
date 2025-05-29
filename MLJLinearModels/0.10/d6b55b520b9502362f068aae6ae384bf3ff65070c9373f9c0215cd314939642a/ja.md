LBFGS準ニュートンソルバー。詳細は[ウィキペディアのエントリ](https://en.wikipedia.org/wiki/Limited-memory_BFGS)を参照してください。

`optim_options`は[一般的な最適化オプション](https://julianlsolvers.github.io/Optim.jl/stable/#user/config/)です。`lbfgs_options`は[LBFGSメソッドのオプション](https://julianlsolvers.github.io/Optim.jl/stable/#algo/lbfgs/)です。

## 例

```julia
using MLJLinearModels, Optim

solver = MLJLinearModels.LBFGS(
    optim_options = Optim.Options(time_limit = 20),
    lbfgs_options = (linesearch = Optim.LineSearches.HagerZhang()),)
)
```
