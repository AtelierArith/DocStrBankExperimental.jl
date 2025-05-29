```
compose(lhs::Symbol, rhs::Tuple)
compose(lhs::Symbol, rhs::Term)
compose(lhs::Symbol, rhs::ConstantTerm)
```

変数 `lhs` を予測子 `rhs` のタプルまたはベクターと組み合わせます。

# 引数

  * `lhs::Symbol`: 方程式の左辺。
  * `rhs::Tuple`: 方程式の右辺。

# 戻り値

  * 組み合わされた方程式。

`rhs` が空の場合、関数は `lhs` を切片と組み合わせて返します。そうでない場合、関数は `lhs` を `rhs` の項と組み合わせて返します。
