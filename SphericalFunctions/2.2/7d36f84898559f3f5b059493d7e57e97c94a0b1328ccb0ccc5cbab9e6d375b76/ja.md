```
complex_powers!(zpowers, z)
```

整数の冪 `z^0` から `z^m` までを再帰的に計算します。ここで、`m` は入力 `zpowers` ベクターの長さより1少ない値です。

`z` は正規化されており、複素振幅はおおよそ1であると仮定されています。

参照: [`complex_powers`](@ref)
