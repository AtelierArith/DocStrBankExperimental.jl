```
instrumentnames(o::CausalTable, x::Symbol, y::Symbol)
```

与えられた `CausalTable` オブジェクトから `x` と `y` の因果関係の楽器の名前を出力します。つまり、`x` に関連しているが `y` を引き起こさない変数です。

# 引数

  * `o::CausalTable`: メディエーターの名前を抽出するための `CausalTable` オブジェクト。
  * `x::Symbol`, `y::Symbol`: メディエーターを選択する2つの変数。

# 戻り値

x と y の間のメディエーターの名前を含むシンボルのベクター。
