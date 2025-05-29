```
mediators(o::CausalTable, x::Symbol, y::Symbol)
```

特定の変数ペア (x,y) のための媒介変数を指定された `CausalTable` オブジェクトから選択します。つまり、x によって引き起こされ、y を引き起こす変数です。

# 引数

  * `o::CausalTable`: 媒介変数を抽出するための `CausalTable` オブジェクト。
  * `x::Symbol`, `y::Symbol`: 媒介変数を選択すべき二つの変数。

# 戻り値

x と y の両方の媒介変数のみを含む新しい `CausalTable`。
