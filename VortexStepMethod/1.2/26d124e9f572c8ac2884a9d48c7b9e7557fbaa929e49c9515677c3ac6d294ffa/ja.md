```
init!(body_aero::BodyAerodynamics; init_aero, va, omega)
```

BodyAerodynamics構造体をパネルと係数を設定することでインプレースで初期化します。

# 引数

  * `body_aero::BodyAerodynamics`: 初期化する構造体

# キーワード引数

  * `init_aero::Bool`: 航空データを初期化するかどうか
  * `va=[15.0, 0.0, 0.0]`: 見かけの風ベクトル
  * `omega=zeros(3)`: カイトボディフレームにおける回転率 x, y, z

# 戻り値

何も返さない
