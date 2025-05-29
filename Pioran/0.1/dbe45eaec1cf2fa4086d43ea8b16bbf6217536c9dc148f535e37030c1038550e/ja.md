```
TwoLogUniformDependent(a, b, ϵ) 
TwoLogUniformDependent(a, b) (constructor with default ϵ = 1e-10
```

三つのランダム変数をモデル化する多変量分布で、最初の変数 x1 は log-U[a,b] で与えられ、二つ目の変数 x2 は log-U[x1,b] で与えられます。

  * `a`: 最初の分布の下限
  * `b`: 最初の分布の上限
  * `ϵ`: 各分布の下限と上限が異なることを保証するための小さな値

これは、二つ目の分布の下限が最初の分布の値に依存していることを意味します。これは、動的サポートを持つ依存事前分布に対する現在の Turing の実装の制限を克服するために実装されています。詳細については、以下の問題を参照してください: [[1]](https://github.com/TuringLang/Turing.jl/issues/1558),[[2]](https://github.com/TuringLang/Turing.jl/issues/1708),[[3]](https://github.com/TuringLang/Turing.jl/issues/1270).
