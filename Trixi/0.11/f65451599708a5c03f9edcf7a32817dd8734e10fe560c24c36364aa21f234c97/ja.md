```
entropy2cons(w, equations)
```

エントロピー変数 `w` を標準の [`entropy`](@ref) に基づいて、与えられた `equations` のための保存変数に変換します。`u` は正しい長さ `nvariables(equations)` のベクトル型です。この関数は効率のためにエラーチェックを含まないため、入力が正しいことを確認してください。逆変換は [`cons2entropy`](@ref) によって行われます。
