```
encodingOps_simple(acqData::AcquisitionData, shape::NTuple{D,Int64}
                          ; kargs...) where D
```

は、MRI取得における個々のコントラストの信号エンコーディングを記述するLinearOperatorsの配列を生成します（特定のスライスに対して）。

# 引数

  * `acqData::AcquisitionData`            - AcquisitionDataオブジェクト
  * `shape::NTuple{D,Int64}`              - エンコード/再構成される画像のサイズ
