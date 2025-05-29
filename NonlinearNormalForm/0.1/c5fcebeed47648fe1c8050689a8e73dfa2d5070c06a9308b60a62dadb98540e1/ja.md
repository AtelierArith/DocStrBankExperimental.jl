```
NonlinearNormalForm.DAMap(;use::UseType=GTPSA.desc_current, x::Vector=vars(getdesc(use)), x0::Vector=zeros(eltype(eltype(x)), numvars(use)), Q::Union{Quaternion,Nothing}=nothing, E::Union{Matrix,Nothing}=nothing, idpt::Union{Bool,Nothing}=nothing, spin::Union{Bool,Nothing}=nothing, FD::Union{Bool,Nothing}=nothing)
```

渡された `TPS`/`ComplexTPS64` のベクトルを軌道レイとして使用して `NonlinearNormalForm.DAMap` を構築し、オプションで入口座標 `x0`、スピンのための `Quaternion` `Q`、および FD 行列 `E` をキーワード引数として指定します。ヘルパーキーワード引数 `spin` と `FD` は、単位クォータニオン/FD 行列を持つ `NonlinearNormalForm.DAMap` を構築するために `true` に設定することができ、スピン/FD がない場合は `false` に設定できます。`Q` または `E` が指定されていない状態で `spin`/`FD` を任意の `Bool` 値に設定することは型不安定です。このコンストラクタは、軌道レイと GTPSA `Descriptor` の長さの整合性もチェックします。`use` キーワード引数は、変数の数が一致する限り、TPS の `Descriptor` を変更するためにも使用できます（順序は異なる場合があります）。
