```
variables(model)
variables(model, models...)
```

モデルに必要な変数の名前を含むタプル、または複数のモデルのためのそれらの変数のユニオンを返します。

# 注

各モデルは（そしてすべきです）この関数のためのメソッドを持つことができます。

```jldoctest

using PlantSimEngine;

# パッケージ内の例として与えられたダミーモデルをロードします：
using PlantSimEngine.Examples;

variables(Process1Model(1.0))

variables(Process1Model(1.0), Process2Model())

# 出力

(var1 = -Inf, var2 = -Inf, var3 = -Inf, var4 = -Inf, var5 = -Inf)
```

# 参照

[`inputs`](@ref), [`outputs`](@ref) および [`variables_typed`](@ref)
