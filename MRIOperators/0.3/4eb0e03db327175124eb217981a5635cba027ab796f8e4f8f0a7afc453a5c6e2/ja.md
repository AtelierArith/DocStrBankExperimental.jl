```
encodingOp_multiEcho(acqData::AcquisitionData{T,D}, shape::NTuple{D,Int64}; kargs...) where {T,D}
```

は、MRI取得におけるすべてのコントラストの組み合わせ信号エンコーディングを記述するLinearOperatorを生成します（特定のスライスに対して）。

# 引数

  * `acqData::AcquisitionData`            - AcquisitionDataオブジェクト
  * `shape::NTuple{D,Int64}`              - エンコード/再構成される画像のサイズ
