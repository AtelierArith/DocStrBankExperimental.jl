```
verify(exafmm::ExaFMM{Float32}, fmmoptions::LaplaceFMMOptions{I}) where I
```

関数は評価されたFMM `exafmm` の精度を計算します。

# 引数

  * `exafmmm::ExaFMM{Float32}`: すべての割り当てられた変数へのポインタを持つExaFMM構造体。
  * `fmmoptions::LaplaceFMMOptions{I}`: セットアップ関数のためのJulia Laplace初期化子で、識別子として使用されます。
