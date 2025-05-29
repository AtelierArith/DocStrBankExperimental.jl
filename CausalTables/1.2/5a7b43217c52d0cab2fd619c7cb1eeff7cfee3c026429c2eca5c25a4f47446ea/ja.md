```
confoundernames(o::CausalTable)
```

指定された `CausalTable` オブジェクトから各応答-治療ペアの交絡因子名を出力します。

# 引数

  * `o::CausalTable`: 各治療-応答ペアの交絡因子名を抽出するための `CausalTable` オブジェクト。

# 戻り値

各治療-応答ペアの交絡因子名を含むベクトルの行列。
