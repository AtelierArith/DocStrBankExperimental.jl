```
encodingOps_parallel(acqData::AcquisitionData{T,D}, shape::NTuple{D,Int64}
                          , senseMaps::Array{Complex{T}}
                          ; kargs...) where {T,D}
```

は、MRI取得における個々のコントラストの信号エンコーディングを記述するLinearOperatorsの配列を生成します。異なるコイルは、その感度に基づいて考慮されます。

# 引数

  * `acqData::AcquisitionData{T,D}`       - AcquisitionDataオブジェクト
  * `shape::NTuple{D,Int64}`              - エンコード/再構成される画像のサイズ
  * `senseMaps::Array{Complex{T}}`        - コイル感度
