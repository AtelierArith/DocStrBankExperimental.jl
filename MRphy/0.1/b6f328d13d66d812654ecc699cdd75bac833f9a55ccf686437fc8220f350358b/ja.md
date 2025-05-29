```
B = rfgr2B(rf, gr, loc=[0 0 0]u"cm"; Δf=0u"Hz", b1Map=1, γ=γ¹H)
```

rf、`rf`、および勾配、`gr`を𝐵-効果的磁場に変換します。

*入力*:

  * `rf::TypeND(RF0D, [1,2])` (nT, (nCoil))
  * `gr::TypeND(GR0D, [2])`   (nT, 3)
  * `loc::TypeND(L0D, [2])`   (1,3) または (nM, 3)、位置。

*キーワード*:

  * `Δf::TypeND(F0D, [0,1,2])` (1,)  または (nM,), オフレゾナンス。
  * `b1Map::TypeND(Union{Real,Complex},[0,1,2])` (1,) または (nM,(nCoils)), 送信感度。
  * `γ::TypeND(Γ0D, [0,1])` (1,)  または (nM,), ジャイロ比

*出力*:

  * `B`, `TypeND(B0D, [2])` (1,1,nT) の生成物、𝐵フィールド。

参照: [`Pulse2B`](@ref), [`blochSim`](@ref)。

# TODO:

`loc`、`Δf`、および `b1Map` が `Base.Generators` であることをサポートします。
