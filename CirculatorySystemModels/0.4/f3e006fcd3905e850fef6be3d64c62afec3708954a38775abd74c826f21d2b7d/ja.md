`MynardValve_SemiLunar(; name, ρ, Leff, Mrg, Mst, Ann, Kvc, Kvo)`

半月弁を通る流れのためのMynard記述を実装します。詳細は[Mynard]を参照してください。この弁の記述は、慣性が考慮される半月弁に対応しています。

注意: 逆流の最小レベルは機械精度eps()に設定する必要があります。

パラメータはcm、g、sシステムで表されます。圧力はmmHgで、流量はcm^3/s (ml/s)で、pは単位が一貫するようにスケーリングされています。

名前付きパラメータ:

name    要素の名前 `ρ`     血液密度 (g/cm^3) `Leff`  有効長 (cm) `Mrg`   弁が示す逆流のレベル (DN) `Mst`   弁が示す狭窄のレベル (DN) `Ann`   環状面積 (cm^2) `Kvc`   弁閉鎖速度係数 (cm^2/(dynes*s)) `Kvo`   弁開放速度係数 (cm^2/(dynes*s))

pはmmHgで計算され、qはcm^3/s (ml/s)で計算されます。
