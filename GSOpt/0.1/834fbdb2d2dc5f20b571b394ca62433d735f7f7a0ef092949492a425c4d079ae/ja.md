```
JuMP.num_constraints(model::AbstractSpGpModel, function_type=nothing, set_type=nothing; 
                     count_variable_in_set_constraints::Bool = true) -> Int
```

モデル内の制約の数を返します。

# 引数

  * `model::AbstractSpGpModel`: 幾何学的プログラミングモデル
  * `function_type`: カウントする制約関数のオプションタイプ
  * `set_type`: カウントする制約セットのオプションタイプ
  * `count_variable_in_set_constraints::Bool`: 変数の境界を制約としてカウントするかどうか

# 戻り値

  * 指定されたタイプに一致する制約の数、またはタイプが指定されていない場合はすべての制約の数
