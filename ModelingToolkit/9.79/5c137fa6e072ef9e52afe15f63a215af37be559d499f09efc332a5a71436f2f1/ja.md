```
getdist(x)
```

シンボリック変数 `x` に関連付けられた確率分布を取得します。`x` に関連付けられた分布がない場合、`nothing` が返されます。次のように関連付けられた分布を持つパラメータを作成します。

```julia
using Distributions
d = Normal(0, 1)
@parameters u [dist = d]
hasdist(u) # true
getdist(u) # 分布を取得
```
