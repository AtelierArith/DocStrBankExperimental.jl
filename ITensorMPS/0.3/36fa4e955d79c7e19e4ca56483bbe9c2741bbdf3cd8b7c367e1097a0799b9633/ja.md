```
ITensors.set_ortho_lims!(::MPS/MPO, r::UnitRange{Int})
```

MPS/MPOの直交中心のサイトの範囲を設定します。

これはエクスポートされておらず、注意して使用すべき高度な機能です。直交制限を誤って設定すると、ITensor MPS/MPO関数を使用する際に不正確な結果をもたらす可能性があります。

MPS/MPOを変更して直交制限を保持したい場合は、`@preserve_ortho`マクロを参照してください。
