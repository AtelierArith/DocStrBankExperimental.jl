```
verify(exafmm::ExaFMM{Float64}, fmmoptions::ModifiedHelmholtzFMMOptions{I, Float64})
```

関数は評価されたFMM `exafmm` の精度を計算します。

# 引数

  * `exafmmm::ExaFMM{Float64}`: すべての割り当てられた変数へのポインタを持つExaFMM構造体。
  * `fmmoptions::ModifiedHelmholtzFMMOptions{I, Float64}`: セットアップ関数のためのJulia修正ヘルムホルツ初期化子で、識別子として使用されます。
