```julia
System(
    parms::ActinRingsMC.SystemParams,
    filaments::Vector{ActinRingsMC.Filament},
    radius::Float64
) -> ActinRingsMC.System

```

システムデータ、パラメータとフィラメントの位置を含みます。

指定された半径は、格子を作成するために使用される格子の高さに対応するものであり、フィラメントの初期構成に対応する必要があります。
