```
LoadLimits{T<:Real} <: AbstractLoadLimits{T}
```

ノードの容量利用に制限を設けるための型で、変数[`:cap_use`](@extref EnergyModelsBase man-opt_var-cap)を制約します。

# フィールド

  * **`min`** は、設置された容量の割合としての最小負荷です。
  * **`max`** は、設置された容量の割合としての最大負荷です。
