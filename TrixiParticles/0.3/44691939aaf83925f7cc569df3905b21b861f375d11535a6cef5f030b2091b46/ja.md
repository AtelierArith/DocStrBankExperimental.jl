```
ViscosityMorris(; nu, epsilon=0.01)
```

モリスによる粘度 [Morris (1997)](@cite Morris1997) は [Fourtakas (2019)](@cite Fourtakas2019) にも使用されています。

実装された粘度モデルの概要と比較については、[`Viscosity`](@ref viscosity_sph) を参照してください。

# キーワード

  * `nu`: 動粘度
  * `epsilon=0.01`: 特異点を防ぐためのパラメータ
