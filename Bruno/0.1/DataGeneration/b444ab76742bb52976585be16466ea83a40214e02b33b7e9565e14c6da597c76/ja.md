```
opt_block_length(array, bootstrap_method::TSBootMethod)
```

時系列ブロックブートストラップの最適ブロック長を、PolitisとWhite（2004）によって定義された方法を使用して計算します。

StationaryまたはCircularBlock以外のブートストラップメソッドが使用される場合、関数はCircularBlockにデフォルト設定されます。

# 例

```julia
using Distributions: Normal

# ar(1)データセットを作成
ar1 = [1.0];
for _ in 1:799
    push!(ar1, ar1[end] * 0.7 + rand(Normal()))
    end

# 最適ブロック長を見つける
st_bl = opt_block_length(ar1, Stationary)
cb_bl = opt_block_length(ar1, CircularBlock)
```
