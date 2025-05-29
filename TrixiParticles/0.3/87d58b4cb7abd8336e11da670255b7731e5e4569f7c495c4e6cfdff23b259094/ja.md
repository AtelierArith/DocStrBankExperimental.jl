```
PressureMirroring()
```

`density_calculator` for `BoundaryModelDummyParticles`.

!!! note
    この境界モデルは、WCSPHとの安定性のために高い粘度を必要とします。また、[`AdamiPressureExtrapolation`](@ref)よりも著しく悪い結果を生み出し、圧力のノイズが増えるため、より小さな時間ステップが必要となるため、効率的でもありません。このモデルは、研究目的および[ SPlisHSPlasH](https://github.com/InteractiveComputerGraphics/SPlisHSPlasH)との比較のためにのみ追加されました。

