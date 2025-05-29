Newton solver. これは完全なヘッセ行列ソルバーであり、「大規模」ケースでは避けるべきです。

`optim_options` は [一般的な最適化オプション](https://julianlsolvers.github.io/Optim.jl/stable/#user/config/) です。 `newton_options` は [ニュートン法のオプション](https://julianlsolvers.github.io/Optim.jl/stable/#algo/newton/) です。

## 例

```julia
using MLJLinearModels, Optim

solver = MLJLinearModels.Newton(
    optim_options = Optim.Options(time_limit = 20),
    newton_options = (linesearch = Optim.LineSearches.HagerZhang()),)
)
```
