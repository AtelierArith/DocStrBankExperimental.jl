```julia
prepareSAS2DFactor(
    totalPhones,
    csvWaveData;
    cfgd,
    rangemodel,
    chirpFile
)

```

SAS配列のサイズである`totalPhones`を使用して、ファクターグラフで使用するsas2dファクターを準備します。 より高速なロード時間のために、既知の`cfgd::Dict{String,}`を渡します。
