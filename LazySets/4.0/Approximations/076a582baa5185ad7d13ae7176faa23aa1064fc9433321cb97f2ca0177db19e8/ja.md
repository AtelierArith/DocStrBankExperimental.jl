```
overapproximate(X::S, ::Type{S}, args...) where {S<:LazySet}
```

型 `S` の集合を型 `S` で上近似することは、何もしない操作です。

### 入力

  * `X`       – 集合
  * `Type{S}` – 目標集合型
  * `args`    – さらなる引数（無視されます）
  * `kwargs`  – さらなるキーワード引数（無視されます）

### 出力

入力された集合。
