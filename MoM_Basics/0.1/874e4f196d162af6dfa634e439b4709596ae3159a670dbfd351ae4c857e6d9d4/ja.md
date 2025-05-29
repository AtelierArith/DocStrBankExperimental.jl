```
AntennaArray{FT<:Real, AT, N} <: AbstractAntennaArray
```

機械走査アレイアンテナ (mechanically scanned array, MSA)、フェーズドアレイ (Phased Array) アレイアンテナはオイラー角を使用しており、参考[`eulerRotationMat`](@ref) 注意アレイの初期指向は提供されたアンテナ素子によって合成され、アレイとしては指向の回転のみを提供します。
