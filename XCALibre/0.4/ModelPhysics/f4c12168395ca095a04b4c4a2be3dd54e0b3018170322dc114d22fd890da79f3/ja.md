```
Ttoh!(model::Physics{T1,F,M,Tu,E,D,BI}, T::ScalarField, h::ScalarField
) where {T1,F<:AbstractCompressible,M,Tu,E,D,BI}
```

関数は温度スカラー場を有効エンタルピーのスカラー場に変換します。

### 入力

  * `model`  – ユーザーによって定義された物理モデル。
  * `T`      – 温度スカラー場。
  * `h`      – 有効エンタルピーのスカラー場。
