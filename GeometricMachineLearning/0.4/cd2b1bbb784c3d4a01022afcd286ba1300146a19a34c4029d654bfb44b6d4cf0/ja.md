```
LASympNet(d)
```

次元 $d$ の $LA$-SympNet を作成します。

[`DataLoader`](@ref) のインスタンスを供給することで呼び出すことができる追加のコンストラクタがあります。

# 例

```jldoctest
using GeometricMachineLearning
dl = DataLoader(rand(2, 20); suppress_info = true)
LASympNet(dl)

# 出力

LASympNet{typeof(tanh), true, true}(2, 5, 1, tanh)
```

# 引数

キーワード引数は次のとおりです：

  * `depth::Int = 5`: 適用される線形層の数。
  * `nhidden::Int = 1`: 隠れ層の数（すなわち、出力層ではない層）。
  * `activation = tanh`: 適用される活性化関数。
  * `init_upper_linear::Bool = true`: 線形層を初期化して、最初に $q$-成分を修正するようにします。
  * `init_upper_act::Bool = true`: 活性化層を初期化して、最初に $q$-成分を修正するようにします。
