```
`regrid(acqData::AcquisitionData{T}, kspaceSize::NTuple{2,Int64}
          ; cgnr_iter::Int64=3, correctionMap::Array{Complex{T}}=Complex{T}[]) where (D,T)`

`acqData`の非Cartesian k空間データをサイズ`kspaceSize`のCartesianグリッドに再グリッドします。非Cartesianフーリエエンコーディングを反転するためにCGNR法を使用します。

# 引数:

  * `acqData::AcquisitionData{T}`        - AcquisitionData
  * `ksize::NTuple{2,Int64}`          - Cartesian k空間グリッドのサイズ
  * `cgnr_iter::Int64=3`              - CGNRイテレーションの数
  * `correctionMao::Array{Complex{T}}`- リラクゼーション/b0マップ
```
