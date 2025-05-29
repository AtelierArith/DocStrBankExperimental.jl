```
encodingOp_multiEcho_parallel(acqData::AcquisitionData{T,D}, shape::NTuple{D,Int64}
                                      , senseMaps::Array{Complex{T}}
                                      ; kargs...) where {T,D}
```

は、MRI取得におけるすべてのコントラストの結合信号エンコーディングを記述するLinearOperatorを生成します（特定のスライスに対して）。異なるコイルは、その感度に基づいて考慮されます。

# 引数

  * `acqData::AcquisitionData{T,D}`       - AcquisitionDataオブジェクト
  * `shape::NTuple{2,Int64}`              - エンコード/再構成される画像のサイズ
  * `senseMaps::Array{Complex{T}}`        - コイル感度
