```
value(uvs::UncertainValues, lbl::Label)
value(uvs::UncertainValues, lbl::Label, defValue)
```

Labelに関連付けられた値。最初の実装は`lbl`が存在しない場合に例外をスローしますが、2番目の実装は`defValue`を返します。
