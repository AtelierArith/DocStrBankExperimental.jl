```
outputs(model::AbstractModel)
outputs(...)
```

1つまたは複数のモデルの出力を取得します。

デフォルトでは、`AbstractModel`（出力なし）または`Missing`モデルの場合、空のタプルを返します。

# 例

```jldoctest
using PlantSimEngine;

# パッケージの例として与えられたダミーモデルをロードします：
using PlantSimEngine.Examples;

outputs(Process1Model(1.0))

# 出力
(:var3,)
```
