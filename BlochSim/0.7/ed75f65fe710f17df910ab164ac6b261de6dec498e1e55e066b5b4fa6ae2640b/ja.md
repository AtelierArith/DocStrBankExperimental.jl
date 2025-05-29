```
spgr! = SPGRBlochSim(TR, TE, rf, [spoiling], [nTR], [save_transients])
spgr!(spin, [workspace])
```

スピンの磁化ベクトルを上書きして、スプイールドグラデイントリコールエコー（SPGR）スキャンをシミュレートします。結果の磁化は `spin.M` に保存されます。`nTR > 0` かつ `save_transients === true` の場合、`spgr!(...)` はシミュレートされた各 `nTR` の TR のエコー時間での磁化ベクトルを持つ `Vector` を返します。

# 引数

  * `TR::Real`: 繰り返し時間 (ms)
  * `TE::Real`: エコー時間 (ms)
  * `rf`:

      * `::Real`: 刺激フリップ角 (rad) (瞬時RFパルスを仮定)
      * `::AbstractRF`: 刺激RFパルス
  * `spoiling::AbstractSpoiling = IdealSpoiling()`: 適用するスプイリングのタイプ
  * `nTR::Val = Val(0)`: シミュレートするTRの数; `Val(0)` は定常状態スキャンをシミュレートすることを示します
  * `save_transients::Val = Val(false)`: シミュレートされた各 `nTR` の TR の TE での磁化ベクトルを返すかどうか; `nTR == 0` の場合は何もしません

`workspace isa SPGRBlochSimWorkspace`。
