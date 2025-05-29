```
ModelMode
```

JuMPモデル内のCachingOptimizerの状態を説明するための列挙型です。

参照: [`mode`](@ref)。

## 値

可能な値は次のとおりです：

  * [`AUTOMATIC`]: `moi_backend`フィールドはAUTOMATICモードのCachingOptimizerを保持します。
  * [`MANUAL`]: `moi_backend`フィールドはMANUALモードのCachingOptimizerを保持します。
  * [`DIRECT`]: `moi_backend`フィールドはAbstractOptimizerを保持します。モデルの追加コピーは保存されません。`moi_backend`は`add_constraint`などをサポートしている必要があります。
