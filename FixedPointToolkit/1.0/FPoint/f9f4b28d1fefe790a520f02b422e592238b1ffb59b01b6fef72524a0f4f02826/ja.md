```julia
FixedPoint!(SC::SelfCons; tol::Float64=1e-6, max_iter::Int64=100) 
FixedPoint!(SC::SelfCons, fileName::String; tol::Float64=1e-6, max_iter::Int64=100, checkpoint_interval::Int64 = 10) 
```

`SelfCons` SC に対して固定点反復を実行し、入力ごとに `tol` の収束許容値と `max_iter` の最大反復カットオフを設定します。オプションで、結果をチェックポイントとして保存するために `fileName` を渡すこともできます。チェックポイントの頻度を設定するために、kwarg `checkpoint_interval` を渡すことができます。
