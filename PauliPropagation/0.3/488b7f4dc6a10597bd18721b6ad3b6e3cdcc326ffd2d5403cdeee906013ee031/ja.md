```
set!(psum::Dict{TermType, NodePathProperties}, pstr::TermType, path::NodePathProperties)
```

パウリ和辞書におけるパウリ文字列の係数をインプレースで設定します。パウリ文字列の型は辞書のキータイプ=`TermType`である必要があり、係数`coeff`は値タイプ=`NodePathProperties`である必要があります。係数が0の場合、パウリ文字列は辞書から削除されます。
