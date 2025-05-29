```
prim2cons(u, equations)
```

原始変数 `u` を与えられた `equations` の保存変数に変換します。`u` は正しい長さ `nvariables(equations)` のベクトル型です。この関数は効率のためにエラーチェックを含んでいないので、入力が正しいことを確認してください。逆変換は [`cons2prim`](@ref) によって行われます。
