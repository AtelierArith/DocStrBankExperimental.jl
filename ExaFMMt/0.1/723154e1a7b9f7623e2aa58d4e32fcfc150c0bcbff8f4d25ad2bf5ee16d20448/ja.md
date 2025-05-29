```
verify(exafmm::ExaFMM{ComplexF64}, fmmoptions::HelmholtzFMMOptions{I, ComplexF64}) where I
```

関数は評価されたFMM `exafmm` の精度を計算します。

# 引数

  * `exafmmm::ExaFMM`: すべての割り当てられた変数へのポインタを持つExaFMM構造体。
  * `fmmoptions::HelmholtzFMMOptions{I, ComplexF64}`: セットアップ関数のためのJulia Helmoltz初期化子で、識別子として使用されます。
