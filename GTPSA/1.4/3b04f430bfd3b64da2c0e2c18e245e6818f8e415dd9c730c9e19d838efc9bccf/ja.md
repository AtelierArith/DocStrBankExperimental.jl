```
setTPS!(t::TPS, t1::Number; change::Bool=false) -> t
```

TPS `t` を `t1` に等しく設定する一般的な関数です。`change` が `true` の場合、`t` と `t1` は異なる `Descriptor` を持つことができ（無効な単項式は削除されます）、変数の数 + パラメータの数が等しい限り可能です。
