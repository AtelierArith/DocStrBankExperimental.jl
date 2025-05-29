```
function is_local_norm(K::Hecke.RelSimpleNumField{AbsSimpleNumFieldElem}, a::AbsSimpleNumFieldElem) -> Bool
```

`a`が`K`の係数体の要素であり、イデールの意味での局所ノルムであるかどうかをテストします。すなわち、基底体の完備化を拡張する完備化のノルムの積です。
