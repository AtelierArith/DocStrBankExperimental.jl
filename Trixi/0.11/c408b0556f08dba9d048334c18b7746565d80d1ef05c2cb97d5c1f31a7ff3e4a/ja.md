```
cons2entropy(u, equations)
```

保存された変数 `u` を、選択された標準 [`entropy`](@ref) に対して与えられた `equations` のセットに対するエントロピー変数に変換します。

`u` は、正しい長さ `nvariables(equations)` のベクトル型です。この関数は効率のためにエラーチェックを含まないため、入力が正しいことを確認してください。逆変換は [`entropy2cons`](@ref) によって行われます。
