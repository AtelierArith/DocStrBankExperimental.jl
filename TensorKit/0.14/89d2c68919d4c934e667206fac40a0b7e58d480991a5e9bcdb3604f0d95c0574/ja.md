```
abstract type AbstractTensorMap{T<:Number, S<:IndexSpace, N₁, N₂} end
```

すべてのテンソルマップの抽象スーパタイプ、すなわち、要素型 `T` を持つ `S<:IndexSpace` 型のベクトル空間のテンソル積間の線形マップです。`AbstractTensorMap` は、入力空間 `ProductSpace{S, N₂}` から出力空間 `ProductSpace{S, N₁}` へのマップです。
