```
ReactionNetwork
```

PALEOboxes.Model または反応ネットワークを含む PALEOmodel 出力を分析するための関数

反応速度変数に付随する属性から反応の化学量論と速度情報をコンパイルします：

  * rate_processname::String: プロセス名（例："photolysis"、"reaction"、...）
  * rate_species::Vector{String} 反応物および生成物の種の名前
  * rate_stoichiometry::Vector{Float64} 反応物および生成物の化学量論
