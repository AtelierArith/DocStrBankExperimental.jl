```
mese! = MESEBlochSim(TR, TE, nechoes, [rfex, rfref, rephaser, crusher, spoiling])
mese!(spin, [workspace])
```

`spin`に対して多重エコースピンエコー（MESE）スキャンをシミュレートし、スピンの磁化ベクトルを上書きします。各エコーでの磁化ベクトルを含む`Vector`を返します。

# 引数

  * `TR::Real`: 繰り返し時間（ms）
  * `TE::Real`: 最初のエコー時間およびエコー間隔（ms）；最初のエコー時間は励起パルスの中央から測定されます
  * `nechoes::Integer`: 読み出すエコーの数
  * `rfex::AbstractRF = InstantaneousRF(π/2)`: 励起RFパルス
  * `rfref::AbstractRF = InstantaneousRF(π, -π/2)`: 再焦点化RFパルス
  * `rephaser::Union{<:GradientSpoiling,Nothing} = nothing`: スライス選択励起再位相勾配
  * `crusher::Union{<:GradientSpoiling,Nothing} = nothing`: クラッシャー勾配（各再焦点化パルスの両側に配置）
  * `spoiling::Union{IdealSpoiling,<:GradientSpoiling,Nothing} = IdealSpoiling()`: 適用するスプーリングの種類

`workspace isa MESEBlochSimWorkspace`。
