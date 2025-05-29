```
psiangles(element, residue_selectors...)
```

`StructuralElementOrList`のpsi角の`Vector`を計算します。

角度を計算できない残基（例えば、原子が欠けている場合や隣接する残基がない場合）には`NaN`が設定されます。角度は-πからπの範囲です。追加の引数は残基セレクタ関数であり、関数から`true`を返す残基のみが保持されます。
