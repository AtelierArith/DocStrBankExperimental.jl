```
NonlinearNormalForm.TPSAMap(;use::UseType=GTPSA.desc_current, x::Vector=vars(getdesc(use)), x0::Vector=zeros(eltype(eltype(x)), numvars(use)), Q::Union{Quaternion,Nothing}=nothing, E::Union{Matrix,Nothing}=nothing, idpt::Union{Bool,Nothing}=nothing, spin::Union{Bool,Nothing}=nothing, FD::Union{Bool,Nothing}=nothing)
```

渡された `TPS`/`ComplexTPS64` のベクトルを軌道レイとして使用して、NonlinearNormalForm.TPSAMap を構築します。オプションで、入口座標 `x0`、スピンのための `Quaternion` `Q`、および FD 行列 `E` をキーワード引数として指定できます。ヘルパーキーワード引数 `spin` と `FD` は、単位クォータニオン/FD 行列を持つ NonlinearNormalForm.TPSAMap を構築するために `true` に設定することができ、スピン/FD を持たないために `false` に設定することもできます。`Q` または `E` が指定されていない状態で `spin`/`FD` を任意の `Bool` 値に設定すると、型が不安定になります。このコンストラクタは、軌道レイと GTPSA `Descriptor` の長さの一貫性もチェックします。`use` キーワード引数は、TPS の `Descriptor` を変更するためにも使用でき、変数の数が一致する限り（次数は異なる場合があります）。
