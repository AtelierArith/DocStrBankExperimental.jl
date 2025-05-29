```
Exp{T}(start, decay)
Exp(; start, decay)
```

指数減衰スケジュールで、レートは `decay` です。出力は次の式に従います。

```text
start * decay^{t - 1}
```

# 引数:

  * `start`: 基本値
  * `decay`: 減衰率
