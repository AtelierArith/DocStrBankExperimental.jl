```
covariate(src, group_a, [group_b])
```

`src`を参照して、`group_a`と`group_b`を比較する二群の`covariate`を作成します。

`src`は次のいずれかです：

  * `String` - DataMatrix `obs`の列を参照します。
  * `DataFrame` - 正確に2列を持ち、最初の列は`obs`のIDと一致するIDを含み、2番目の列は共変量を含みます。
  * `Annotations`（実験的） - DataMatrix `obs`と一致するIDを持ち、共変量のための2番目の列を持ちます。

`src`が`String`の場合、それはDataMatrix `obs`の列を参照します。`src`はまた、DataMatrix `obs`と一致するIDを持つ`Annotations`オブジェクトであることもできます。`group_a`と`group_b`は、列`src`に出現する値でなければなりません。

`group_b`が指定されていない場合、`group_a`は他のすべての観察と比較されます。

参照： [`designmatrix`](@ref)
