```
reconstruction(acqData::AcquisitionData, recoParams::Dict,filename::String; force=false)
```

は、`reconstruction(acqData::AcquisitionData, recoParams::Dict)` と同じ画像再構成を行い、画像を `filename` という名前のファイルに保存します。`force=false` の場合、再構成された画像は、後者が存在する場合にファイル `filename` から読み込まれます。
