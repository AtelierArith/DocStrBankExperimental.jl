```
OrderSlices!(rawData::RawAcquisitionData)
```

MRIReco.jlの生データ構造内のスライスを空間的に順序付けます。スライスは、各プロファイルに保存された位置座標に基づいて順序付けられます。これらが存在しない場合、スライスを順序付けることはできません。

MRIRecoの参考文献: https://onlinelibrary.wiley.com/doi/epdf/10.1002/mrm.28792

# 引数

  * `rawData::RawAcquisitionData` - MRIReco.jlを使用して生データをロードすることで得られる生データ構造
