```
cons2prim(u, equations)
```

保存変数 `u` を与えられた `equations` のセットに対する原始変数に変換します。`u` は正しい長さ `nvariables(equations)` のベクトル型です。この関数は効率のためにエラーチェックを含まないため、入力が正しいことを確認してください。逆変換は [`prim2cons`](@ref) によって行われます。
