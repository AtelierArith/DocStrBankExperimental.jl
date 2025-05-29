```
reconstruction(acqData::AcquisitionData, recoParams::Dict)
```

AcquisitionDataオブジェクトの画像再構成を行います。パラメータは辞書で指定されます。

再構成タイプはシンボル`:reco`で指定されます。有効な再構成名は次のとおりです：

  * :direct - 直接フーリエ再構成
  * :standard           - すべてのコントラスト、コイル、スライスを独立して反復再構成
  * :multiEcho          - すべてのエコー画像の反復共同再構成
  * :multiCoil          - SENSE型反復再構成
  * :multiCoilMultiEcho - すべてのエコー画像のSENSE型反復再構成
