```
inner(M::AbstractPowerManifold, p, X, Y)
```

`p`における[`AbstractPowerManifold`](@ref) `M`の接空間からの`X`と`Y`の内積を計算します。すなわち、各配列のエントリについて、`X`と`Y`の接ベクトルエントリは`p`の対応する要素の接空間にあります。内積は、要素ごとの内積の合計となります。
