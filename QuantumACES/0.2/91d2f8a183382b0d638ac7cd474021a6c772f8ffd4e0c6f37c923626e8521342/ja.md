```
is_additive(g::Gate; strict::Bool = false)
```

ゲート `g` に関連するノイズが加法的精度でのみ推定できる場合は `true` を返し、それ以外の場合は `false` を返します。`strict` が `true` の場合、これは状態準備および測定ノイズに対してのみ `true` となります。そうでない場合は、中間回路測定およびリセットノイズ、測定アイドルノイズに対しても `true` となります。
