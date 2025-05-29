```
entanglement_spectrum(ψ, site::Int) -> SectorDict{sectortype(ψ),Vector{<:Real}}
```

与えられたサイトでのエンタングルメントスペクトルを計算します。すなわち、与えられたサイトの右側にあるゲージ行列の特異値です。これは、電荷を特異値にマッピングする辞書です。

`InfiniteMPS` と `WindowMPS` の場合、`site` のデフォルト値は 0 です。

`FiniteMPS` では、`site` のデフォルト値は指定されておらず、ユーザーが指定する必要があります。
