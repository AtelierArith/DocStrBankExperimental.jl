```
FluxHydrostaticReconstruction(numerical_flux, hydrostatic_reconstruction)
```

!!! warning "実験的なコード"
    この数値フラックスは実験的であり、将来のリリースで変更される可能性があります。


表面フラックス計算の前に、解の状態のいくつかの種類の静水圧再構成を許可します。これは、浅水方程式に対してメソッドがバランスを保つことを保証するための特定の戦略です。詳細は[`ShallowWaterEquations1D`](@ref)または[`ShallowWaterEquations2D`](@ref)を参照してください。

例えば、Audusseらによる静水圧再構成は、1次元および2次元の空間で実装されています。詳細は[`hydrostatic_reconstruction_audusse_etal`](@ref)または元の論文を参照してください。

  * Emmanuel Audusse, François Bouchut, Marie-Odile Bristeau, Rupert Klein, and Benoit Perthame (2004) 浅水流のための静水圧再構成を用いた高速かつ安定したバランスの取れたスキーム [DOI: 10.1137/S1064827503431090](https://doi.org/10.1137/S1064827503431090)

他の静水圧再構成技術も利用可能で、特に湿潤/乾燥前線を扱うためのものです。静水圧再構成の開発と応用に関する良い概要は以下にあります。

  * Guoxian Chen and Sebastian Noelle 浅水方程式のための統一された表面勾配および静水圧再構成スキーム (2021) [RWTH Aachen preprint](https://www.igpm.rwth-aachen.de/forschung/preprints/517)
  * Andreas Buttinger-Kreuzhuber, Zsolt Horváth, Sebastian Noelle, Günter Blöschl and Jürgen Waser (2019) 急峻な地形上の二次元構造グリッドにおける高速な二次浅水スキーム [DOI: 10.1016/j.advwatres.2019.03.010](https://doi.org/10.1016/j.advwatres.2019.03.010)
