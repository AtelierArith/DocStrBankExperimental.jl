```julia
get_code_unsafe(modulation, system, phase, prn)

```

PRN `prn` の位相 `phase` における LOC のコードを取得します。位相はコードの長さによってラップされることはありません。位相は、二次コードを含むコードの長さよりも小さくなければなりません。
