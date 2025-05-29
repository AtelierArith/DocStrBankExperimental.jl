```
module KrylovDefaults
    const orth = KrylovKit.ModifiedGramSchmidtIR()
    const krylovdim = Ref(30)
    const maxiter = Ref(100)
    const tol = Ref(1e-12)
    const verbosity = Ref(KrylovKit.WARN_LEVEL)
end
```

Krylovベースのアルゴリズムにおける典型的なパラメータのデフォルト値をリストしたモジュール：

  * `orth = ModifiedGramSchmidtIR()`: `Lanczos`または`Arnoldi`反復でKrylov基底を直交化するために使用される直交化ルーチン
  * `krylovdim = 30`: 構築されるKrylov部分空間の最大次元
  * `maxiter = 100`: 外部反復の最大数、すなわちKrylov部分空間が再構築される最大回数
  * `tol = 1e-12`: 問題を解決するための許容誤差、適切な誤差測定に基づく、例えばいくつかの残差のノルム。

!!! warning
    `tol`のデフォルト値は`Float64`値です。`Float32`または`ComplexF32`算術で問題を解決する場合は、デフォルト値が達成できないため、新しい`tol`を常に指定する必要があります。

