```
Poly{T, S<:Integer}(start, degree, max_iter)
Poly(; start, degree, max_iter)
```

多項式スケジュールは、次数 `degree` に従って減衰します。出力は次の式に従います。

```text
start / (1 - (t - 1) / max_iter)^degree
```

# 引数

  * `start`: 基本値
  * `degree::Integer`: 多項式の次数
  * `max_iter::Integer`: 総反復回数

```
