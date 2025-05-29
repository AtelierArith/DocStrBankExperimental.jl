```
検出器
```

X線検出器の特性を定義する抽象型。

実装：

```
channelcount(det::Detector)::Int
scale(det::Detector)::EnergyScale
resolution(eV::Float64, det::Detector)::Float64 # eVでのFWHM
energy(ch::Int, det::Detector)::Float64
channel(eV::Float64, det::Detector)::Int
profile(energy::Float64, xrayE::Float64, det::Detector)
lld(det::Detector)::Int
isvisible(sf::SpectrumFeature, det::Detector)
```
