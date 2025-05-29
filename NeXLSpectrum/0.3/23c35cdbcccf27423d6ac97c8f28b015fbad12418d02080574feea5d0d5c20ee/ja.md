```
references(refs::AbstractVector{ReferencePacket}, det::EDSDetector)::FilterFitPacket
references(refs::AbstractVector{ReferencePacket}, fwhm::Float64)::FilterFitPacket
```

`ReferencePackets`のベクターから`FilterFitPacket`を構築します。各`ReferencePacket`は、要素の単一ROIを表します。元素ROIに対して複数の`ReferencePacket`が定義される可能性があります。この場合、インデックスが低い`ReferencePacket`が後のものよりも優先されます。これにより、代替材料から収集したスペクトルを使用して、欠落している元素ROIのみを埋めることができます。たとえば、F₂FeからのスペクトルはFe K線には適していますが、Fe L線には適していません。したがって、最初にF₂Feを指定してFe K線の参照を指定し、その後、純粋なFeからのスペクトルでL線を埋めることができます。
