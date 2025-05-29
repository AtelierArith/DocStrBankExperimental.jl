```
corner!(p::Path, α, sty::Style=discretestyle1(p))
```

パス `p` に角度 `α` の鋭いターンまたは「コーナー」を追加します。

指定されていない場合、このコーナーに選択されるスタイルは、パスで最後に使用された `DiscreteStyle` です。
