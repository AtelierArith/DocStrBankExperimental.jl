```
confoundernames(o::CausalTable, x::Symbol, y::Symbol)
```

与えられた `CausalTable` オブジェクトから `x` と `y` の因果関係の交絡因子の名前を出力します。

# 引数

  * `o::CausalTable`: 交絡因子の名前を抽出するための `CausalTable` オブジェクト。
  * `x::Symbol`, `y::Symbol`: 交絡因子を選択すべき2つの変数。

# 戻り値

x と y の間の交絡因子の名前を含むシンボルのベクター。
