```
JuMP.solve_time(model::AbstractSpGpModel) -> Float64
```

モデルを解くのにかかった時間（秒単位）を返します。

# 例外

  * モデルがまだ解かれていない場合はエラーをスローします。
