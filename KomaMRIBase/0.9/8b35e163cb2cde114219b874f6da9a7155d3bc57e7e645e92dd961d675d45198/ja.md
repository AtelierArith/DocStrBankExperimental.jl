```
seqd = discretize(seq::Sequence; sampling_params=default_sampling_params())
```

この関数は、シミュレーションパラメータに基づいてRFおよび勾配時間のリファインメントを持つサンプリングされたSequence構造体を返します。

# 引数

  * `seq`: (`::Sequence`) シーケンス

# キーワード

  * `sampling_params`: (`::Dict{String, Any}`, `=default_sampling_params()`) サンプリングパラメータ辞書

# 返り値

  * `seqd`: (`::DiscreteSequence`) DiscreteSequence構造体
