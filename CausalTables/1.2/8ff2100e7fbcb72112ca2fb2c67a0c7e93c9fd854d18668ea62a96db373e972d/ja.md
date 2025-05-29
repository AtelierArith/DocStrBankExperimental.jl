```
instruments(o::CausalTable, x::Symbol, y::Symbol)
```

指定された変数ペア (x,y) のためのインストゥルメントを与えられた `CausalTable` オブジェクトから選択します。つまり、`x` に関連しているが `y` を引き起こさない変数です。

# 引数

  * `o::CausalTable`: インストゥルメントを抽出するための `CausalTable` オブジェクト。
  * `x::Symbol`, `y::Symbol`: インストゥルメントを選択すべき2つの変数。

# 戻り値

x と y のインストゥルメントのみを含む新しい `CausalTable`。
