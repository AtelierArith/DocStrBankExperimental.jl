```
inputs(model::AbstractModel)
inputs(...)
```

1つまたは複数のモデルの入力を取得します。

デフォルトでは、`AbstractModel`（入力なし）または`Missing`モデルの場合、空のタプルを返します。

# 例

```jldoctest
using PlantSimEngine;

# パッケージ内の例として与えられたダミーモデルをロードします：
using PlantSimEngine.Examples;

inputs(Process1Model(1.0))

# 出力
(:var1, :var2)
```
