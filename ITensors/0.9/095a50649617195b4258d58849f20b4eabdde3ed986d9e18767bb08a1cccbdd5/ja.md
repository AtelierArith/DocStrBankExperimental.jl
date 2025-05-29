```
diag_itensor([::Type{ElT} = Float64, ][flux::QN = QN(), ]is)
diag_itensor([::Type{ElT} = Float64, ][flux::QN = QN(), ]is::Index...)
```

`NDTensors.DiagBlockSparse` ストレージタイプを持つ ITensor を作成し、要素は `zero(ElT)` です。この ITensor は、指定された `flux` に一致する対角ブロックのみを持ちます。

要素タイプが指定されていない場合、デフォルトは `Float64` です。`flux` が指定されていない場合、デフォルトは `QN()` です。
