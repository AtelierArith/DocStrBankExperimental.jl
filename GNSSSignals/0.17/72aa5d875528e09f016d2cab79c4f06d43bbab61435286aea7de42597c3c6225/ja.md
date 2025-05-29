```julia
get_code_unsafe(modulation, system, phase, prn)

```

PRN `prn` の位相 `phase` における BOC のコードを取得します。位相はコードの長さによってラップされることはありません。位相は二次コードを含むコードの長さより小さくなければなりません。
