```
Inv{T, S<:Integer}(start, decay, degree)
Inv(; start, decay, degree)
```

逆に減衰する減衰スケジュールで、レートは `decay` です。出力は次の式に従います。

```text
start / (1 + (t - 1) * decay)^degree
```

# 引数

  * `start`: 基本値
  * `decay`: 減衰率
  * `degree::Integer`: 減衰の度合い
