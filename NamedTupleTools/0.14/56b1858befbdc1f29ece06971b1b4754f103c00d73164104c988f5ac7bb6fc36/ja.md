```
split(namedtuple, symbol(s)|Tuple)
```

2つのnamedtupleを生成します。最初のnamedtupleは2番目の引数にあるフィールドのみを含み、2番目のnamedtupleは2番目の引数にあるフィールドを除いたすべてのフィールドを含みます。`merge(split(nt, ks)...) == nt`が成り立つのは、`ks`が`nt`の最初のフィールドを含む場合です。
