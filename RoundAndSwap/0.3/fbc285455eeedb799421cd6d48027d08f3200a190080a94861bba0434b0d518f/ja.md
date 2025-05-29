```
fix!(models::Array{Model}, to_fix::Array{Symbol}, value = 1)
```

各モデルに対して、to_fix内のすべての変数を1に固定します。

# 引数:

  * `models`: 値を固定するモデル
  * `to_fix`: 固定する変数
  * `value`: 固定する値、デフォルトは1
