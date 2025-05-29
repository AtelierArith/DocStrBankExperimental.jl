```
FourierIntegralFunction(f, s, [prototype=nothing]; alias=false)
```

## 引数

  * `f`: 被積分関数で、入力 `f(x, s(x), p)` を受け取ります
  * `s::AbstractFourierSeries`: 評価するフーリエ級数
  * `prototype`:
  * `alias::Bool`: 系列を `deepcopy` するか（false）、そのまま使用するか（true）を指定します
