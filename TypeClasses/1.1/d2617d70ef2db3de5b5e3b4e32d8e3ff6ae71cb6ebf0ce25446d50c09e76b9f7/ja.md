```
mapn(f, a1::F{T1}, a2::F{T2}, a3::F{T3}, ...) -> F{T}
```

アプリカティブコンテキスト上で関数を適用しますが、単純な値ではありません。`Base.map`に似ていますが、場合によっては意味がわずかに異なります。`TypeClasses.mapn`は、定義されている場合、常に`TypeClasses.flatmap`の意味論に従います。

例えば、`Base.Vector`の場合、`Base.map`関数は入力をジップし、同じ長さをチェックします。一方、`TypeClasses.mapn`は、ジップの代わりにすべての入力の組み合わせを組み合わせます（これはネストされたベクターをフラット化する意味論に準拠しています）。
