```
species <: AbstractSpecies
```

speciesは、NASA 9次多項式係数 `alow` と `ahigh` を保持する構造体で、`Tmid` によって分けられた2つの温度領域のためのものです（ここでは6000 K未満の温度のみを扱うため、通常は2つのT間隔が必要です）。与えられた化学種の分子量 `MW` と生成熱 `Hf` (J/mol) を含みます（298.15 Kで）。

典型的なデータ形式については[こちら](https://shepherd.caltech.edu/EDL/PublicResources/sdt/formats/nasa.html)をご覧ください。
