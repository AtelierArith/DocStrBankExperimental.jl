```
RemoveRef!(rawData::RawAcquisitionData, slices::Union{Vector{Int64}, Nothing}, echoes::Union{Vector{Int64}, Nothing})
```

Siemensスキャナーで位相安定化を行った取得データから参照データを削除します。ナビゲーターに基づく補正の前に適用する必要があります。参照データが画像データの前に取得される場合に必要です。タイムスタンプを確認して、これがデータに必要かどうかを確認してください。Siemensの場合：MatlabのmapVBVDを使用して生データを読み取ることが可能です。削除する参照データはmapVBVDでphasestabRefと呼ばれます。連結が1を超えるシーケンスには堅牢ではありません。繰り返し呼び出すことには堅牢ではなく、rawDataを変更します。

MRIRecoの参考文献: https://onlinelibrary.wiley.com/doi/epdf/10.1002/mrm.28792 mapVBVDの参考文献: https://github.com/CIC-methods/FID-A/blob/master/inputOutput/mapVBVD/README.md

# 引数

  * `rawData::RawAcquisitionData` - MRIReco.jlを使用して生データを読み込むことで得られる生データ構造
