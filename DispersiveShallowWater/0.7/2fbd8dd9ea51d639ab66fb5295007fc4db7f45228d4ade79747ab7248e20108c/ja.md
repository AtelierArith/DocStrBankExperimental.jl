```
prim2cons(q, equations)
```

原始変数 `q` を与えられた `equations` の保存変数に変換します。`q` は正しい長さ `nvariables(equations)` のベクトル型です。効率のためにエラーチェックは含まれていないので、入力が正しいことを確認してください。逆変換は [`cons2prim`](@ref) によって行われます。
