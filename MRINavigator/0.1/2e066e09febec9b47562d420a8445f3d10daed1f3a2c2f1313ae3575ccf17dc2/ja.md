```
loadRawData(params::Dict{Symbol, Any})
```

ISMRMRD形式で保存された生データファイルをMRIReco.jlを使用してjuliaでロードします。ExtractNoiseData!、OrderSlices!、ReverseBipolar!、RemoveRef!を呼び出します。詳細については特定の関数を確認してください。

MRIRecoの参考文献: https://onlinelibrary.wiley.com/doi/epdf/10.1002/mrm.28792 ISMRMRDの参考文献: https://onlinelibrary.wiley.com/doi/epdf/10.1002/mrm.26089

# 引数

  * `params::Dict{Symbol, Any}` - MRINavigatorパラメータ構造体、詳細についてはdefaultNavParams()を確認してください。
