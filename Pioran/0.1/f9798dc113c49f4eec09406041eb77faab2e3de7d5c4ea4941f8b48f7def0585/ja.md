```
ThreeUniformDependent(a, b, c, ϵ)
ThreeUniformDependent(a, b, c) (デフォルト ϵ = 1e-10 のコンストラクタ)
```

三変量分布で、最初の変数 x1 は U[a,b] で与えられ、2 番目の変数 x2 は U[x1,c] で与えられ、3 番目の変数 x3 は U[x2,c] で与えられます。ここで、a<b<c です。

  * `a`: 最初の分布の下限
  * `b`: 最初の分布の上限
  * `c`: 2 番目と 3 番目の分布の上限
  * `ϵ`: 各分布の下限と上限が異なることを保証するための小さな値

これは、2 番目の分布の下限が最初の分布の値に依存し、その後も同様であることを意味します... これは、動的サポートを持つ依存事前分布に対する現在の Turing の実装の制限を克服するために実装されています。詳細については、以下の問題を参照してください: [[1]](https://github.com/TuringLang/Turing.jl/issues/1558),[[2]](https://github.com/TuringLang/Turing.jl/issues/1708),[[3]](https://github.com/TuringLang/Turing.jl/issues/1270).
