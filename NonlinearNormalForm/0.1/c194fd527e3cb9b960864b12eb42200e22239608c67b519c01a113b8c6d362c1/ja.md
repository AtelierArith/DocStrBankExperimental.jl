```
NonlinearNormalForm.TPSAMap(M::AbstractMatrix; use::UseType=GTPSA.desc_current, x0::Vector=zeros(eltype(M), size(M,1)), Q::Union{Quaternion,Nothing}=nothing, E::Union{Matrix,Nothing}=nothing, idpt::Union{Bool,Nothing}=nothing, spin::Union{Bool,Nothing}=nothing, FD::Union{Bool,Nothing}=nothing)
```

この関数は最適化可能です。

`M` は線形インデックスを持つ行列を表す必要があります。

スカラーの行列 `M` を `TaylorMap` の線形部分として渡し、オプションで入口座標 `x0`、スピンのための `Quaternion` `Q`、および FD 行列 `E` をキーワード引数として持つ NonlinearNormalForm.TPSAMap を構築します。ヘルパーキーワード引数 `spin` と `FD` は、単位クォータニオン/FD 行列を持つ NonlinearNormalForm.TPSAMap を構築するために `true` に設定することができ、スピン/FD がない場合は `false` に設定できます。`Q` または `E` が指定されていない状態で `spin`/`FD` を任意の `Bool` 値に設定すると、型が不安定になります。このコンストラクタは、軌道レイと GTPSA `Descriptor` の長さの一貫性もチェックします。
