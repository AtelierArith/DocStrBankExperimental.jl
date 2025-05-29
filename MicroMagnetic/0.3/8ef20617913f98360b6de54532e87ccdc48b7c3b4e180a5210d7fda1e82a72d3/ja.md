```
set_precision(x::Type{<:AbstractFloat}=Float64)
```

マイクロ磁気シミュレーションの精度を設定します。

この関数を使用すると、マイクロ磁気シミュレーションで使用される浮動小数点数の精度を指定できます。デフォルトでは、精度は `Float64` に設定されます。単精度計算が必要な場合は、`Float32` を指定できます。

# 例

```julia
set_precision(Float32)
```
