```
htoT!(model::Physics{T1,F,M,Tu,E,D,BI}, h::ScalarField, T::ScalarField
) where {T1,F<:AbstractCompressible,M,Tu,E,D,BI}
```

関数は感覚エンタルピーのスカラー場を温度のスカラー場に変換します。

### 入力

  * `model`  – ユーザーによって定義された物理モデル。
  * `h`      – 感覚エンタルピーのスカラー場。
  * `T`      – 温度のスカラー場。
