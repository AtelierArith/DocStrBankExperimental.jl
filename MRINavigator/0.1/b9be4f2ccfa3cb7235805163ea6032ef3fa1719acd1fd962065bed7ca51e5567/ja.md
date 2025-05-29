```
noisemat = ExtractNoiseData!(rawData::RawAcquisitionData, flags::Array{Int64})
```

MRIReco.jlの生データからノイズ取得を抽出して返します。ノイズ取得は通常、スライス = 0、コントラスト = 0、繰り返し = 0の最初のプロファイルです。ノイズプロファイルの19番目のフラグ要素は1である必要があります。エラーが発生した場合は、ExtractFlagsで確認してください。

MRIRecoの参考文献: https://onlinelibrary.wiley.com/doi/epdf/10.1002/mrm.28792

# 引数

  * `rawData::RawAcquisitionData` - MRIReco.jlで生データを読み込むことで得られる生データ構造
