```
GaussSystem(U::UnitSystem,μ0,λ,αL=𝟏,l=centi,m=milli,g0=gravity(U))
```

`UnitSystem`を`U`から新たに構築し、電磁オプションを持つ`CGS`用にスケーリングします。最初の3つのオプションは`真空透磁率`、`合理化`、および`ローレンツ`定数の値を設定するためのものです。次の2つのパラメータは`長さ`と`質量`のスケーリングであり、最後のパラメータは`重力`の基準を変更するオプションです。

例には`EMU`、`ESU`、`Gauss`、`LorentzHeaviside`、および`Kennelly`が含まれます。
