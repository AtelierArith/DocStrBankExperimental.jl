```
recod_catbyind(x, lev)
```

カテゴリ変数をレベルのインデックスに再コーディングします。

  * `x` : 置き換えるカテゴリ変数 (n)。
  * `lev` : カテゴリレベルを含むベクター。

例を参照してください。

*警告*: `x` のレベルは `lev` に含まれている必要があります。

## 例

```julia
using Jchemo

lev = ["EHH" ; "FFS" ; "ANF" ; "CLZ" ; "CNG" ; "FRG" ; "MPW" ; "PEE" ; "SFG" ; "SFG" ; "TTS"]
slev = mlev(lev)
[slev 1:length(slev)] 
x = ["EHH" ; "TTS" ; "FRG" ; "EHH"]
recod_catbyind(x, lev)
```
