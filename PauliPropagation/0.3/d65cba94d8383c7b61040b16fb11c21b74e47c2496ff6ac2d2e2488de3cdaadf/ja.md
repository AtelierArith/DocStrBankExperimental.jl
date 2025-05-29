```
set!(psum::PauliSum{TermType, CoeffType}, pstr::TermType, coeff::CoeffType)
```

`PauliSum` 辞書内のパウリ文字列の係数をインプレースで設定します。パウリ文字列の型は辞書のキータイプ `TermType` である必要があり、係数 `coeff` は値タイプ `CoeffType` である必要があります。
