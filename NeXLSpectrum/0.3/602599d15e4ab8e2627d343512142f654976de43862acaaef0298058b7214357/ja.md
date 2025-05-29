```
suitability(elm::Element, mats::AbstractSet{<:Material}, det::Detector; maxE=30.0e3)
suitability(elm::Element, det::Detector; maxE=30.0e3, minC=0.1)
```

`mats` に適した材料がある `Element` の特性 X 線ピークを表形式で示します。第二の形式は、ファイル NeXLCore の "standards.txt" にあるデフォルトの材料セットを使用します。

この関数は、指定された Element のフィッティング基準として適した `Material` を特定するのに役立ちます。NeXLSpectrum が `elm` に関連する特性ピークを、各々独立してフィットされる連続した領域に分割する方法を示します。NeXLSpectrum は、指定された `EDSDetector` の解像度に依存して、各要素をできるだけ多くの独立した領域に分割しようとします。`Material` 内の他の要素と `elm` の間に干渉がある場合、このピークはフィッティング基準として適さなくなります。ただし、類似の基準として使用することはできます。
