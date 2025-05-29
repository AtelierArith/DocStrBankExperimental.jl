CVI_MODULES

# 説明

実装されたCVIのリストで、反復に便利です。各要素はCVIの構造体の省略名であり、空のコンストラクタで反復のためにインスタンス化できます。

例えば：

```julia
using ClusterValidityIndices
instantiated_cvis = [local_cvi() for local_cvi in CVI_MODULES]
```
