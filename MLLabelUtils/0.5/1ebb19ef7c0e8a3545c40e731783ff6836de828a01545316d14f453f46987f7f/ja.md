```
convertlabel(new_encoding, vec::AbstractVector, [old_encoding]) -> (Readonly)MappedArray
```

`vec`に対して、`new_encoding`で指定されたエンコーディングのように見える遅延ビューを作成しますが、実際には`old_encoding`として保持されます。

このメソッドは、ベクトルベースのラベルエンコーディング（ほぼすべての`OneOfK`を除く）にのみ機能します。結果のMappedArrayは、`old_encoding`が`OneVsRest`型でない限り、書き込み可能です。この場合、結果は`ReadonlyMappedArray`になります。
