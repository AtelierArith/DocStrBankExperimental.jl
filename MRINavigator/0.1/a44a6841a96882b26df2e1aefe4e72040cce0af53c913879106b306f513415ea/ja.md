```
SelectEcho!(acqd, idx_echo)
```

取得データ構造から1つ以上のエコーを抽出します

# 引数

  * `acqd::AcquisitionData` - MRIReco.jlを使用して生データを変換して得られた取得データ構造
  * `idx_echo::Vector{Int64}` - 選択するエコーのインデックスを含むベクター（0から始まる）

MRIRecoの参考文献: https://onlinelibrary.wiley.com/doi/epdf/10.1002/mrm.28792
