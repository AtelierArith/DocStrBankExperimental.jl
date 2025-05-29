```julia
prepareSAS2DFactor(
    totalPhones,
    csvWaveData;
    cfgd,
    rangemodel,
    chirpFile
)

```

Prepare a sas2d factor to use in the factor graph where `totalPhones` is the size of the SAS array.  Pass a known `cfgd::Dict{String,} for faster load times.`
