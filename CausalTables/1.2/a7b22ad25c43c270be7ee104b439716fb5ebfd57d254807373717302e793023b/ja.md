```
mediatornames(o::CausalTable, x::Symbol, y::Symbol)
```

与えられた `CausalTable` オブジェクトから `x` と `y` の因果関係の媒介者の名前を出力します。

# 引数

  * `o::CausalTable`: 媒介者の名前を抽出するための `CausalTable` オブジェクト。
  * `x::Symbol`, `y::Symbol`: 媒介者を選択する2つの変数。

# 戻り値

x と y の間の媒介者の名前を含むシンボルのベクター。
