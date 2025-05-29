```
SurfaceTensionMomentumMorris(surface_tension_coefficient=1.0)
```

このモデルは、Morris [Morris2000](@cite) によって概説された運動量保存の表面張力アプローチを実装しています。応力テンソルのダイバージェンスを使用して表面張力を計算し、線形運動量の正確な保存を保証します。この方法は、運動量保存が重要なシミュレーションに特に有用ですが、高解像度では数値的な調整が必要になる場合があります。

詳細については [`surface_tension`](@ref) を参照してください。

# キーワード

  * `surface_tension_coefficient=1.0`: 表面張力の強さを調整するためのパラメータで、物理的な挙動を再現するための微調整を可能にします。
