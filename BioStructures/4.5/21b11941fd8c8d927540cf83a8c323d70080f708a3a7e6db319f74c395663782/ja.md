```
ramachandranangles(element, residue_selectors...)
```

`StructuralElementOrList`のφおよびψ角の`Vector`を計算します。

角度を計算できない残基には`NaN`が設定されます。これは、原子が欠けている場合や隣接する残基がない場合などです。角度は-πからπの範囲です。追加の引数は残基セレクタ関数であり、関数から`true`が返される残基のみが保持されます。
