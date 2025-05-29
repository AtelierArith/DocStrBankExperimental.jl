```
chiangles(element, residue_selectors...)
```

`StructuralElementOrList`内の各残基に対する標準χ角の`Vector`を計算します。これは、すべての角度が-πからπの範囲にある`Vector`の`Vector`を返します。追加の引数は残基セレクタ関数であり、関数から`true`を返す残基のみが保持されます。
