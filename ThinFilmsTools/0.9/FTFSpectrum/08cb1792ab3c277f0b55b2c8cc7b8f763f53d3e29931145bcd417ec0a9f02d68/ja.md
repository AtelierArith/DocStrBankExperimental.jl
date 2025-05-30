```
転送行列法で計算された偏光平均理論スペクトルを返します。これは、最初の媒質に当たる光を考慮します (incidentRI)。

    X = theoretical_spectrum(specType, beam, incidentRI, emergentRI)

        specType: 計算するスペクトルのタイプ、Reflectance() または Transmittance()。
        beam: PlaneWave 構造体。
        incidentRI: 複数の波長に対する入射材料の屈折率を含む配列。
            例えば、RIdb.air(beam.λ)。
        emergentRI: 複数の波長に対する出射材料の屈折率を含む配列。
            例えば、RIdb.silicon(beam.λ)。
        X: 平均スペクトル = beam.p*Xp + (1.0 - beam.p)*Xs
```
