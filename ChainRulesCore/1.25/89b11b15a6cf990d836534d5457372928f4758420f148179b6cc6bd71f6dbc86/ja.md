```
is_inplaceable_destination(x) -> Bool
```

`x`が勾配のインプレース蓄積を格納するのに適している場合はtrueを返します。配列の場合、これは`x .= y`が`y`が適切な接線であれば`x`を変更することを意味します。

ここで「適切」とは、`y`が複素数であってはならず、`x`もそうでない限り、また`x`が`Diagonal`のような構造化行列である場合、`y`がこの構造を共有することを意味します。

!!! note "history"
    ラッパー配列タイプは、書き込むことができる場合、この関数をオーバーロードする必要があります。ChainRulesCore 1.16以前は、`parent`に基づいてほとんどのラッパーに対して`true`を推測していましたが、これは安全ではなく、例えばReadOnlyArrays.jlでエラーを引き起こすことになります。


常に正しい非変更パスが存在しなければならないため、不確実な場合、この関数は`false`を返します。
