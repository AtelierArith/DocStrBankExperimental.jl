# NelderMead

## コンストラクタ

```julia
NelderMead(; parameters = AdaptiveParameters(),
             initial_simplex = AffineSimplexer())
```

コンストラクタは2つのキーワードを取ります：

  * `parameters`、`AdaptiveParameters`または`FixedParameters`のいずれかのインスタンス、

Nelder-Meadアルゴリズムのためのパラメータを生成するために使用されます。

  * `initial_simplex`、`AffineSimplexer`のインスタンス

## 説明

私たちの現在のNelder-Meadアルゴリズムの実装は[1]および[3]に基づいています。勾配フリーの手法は、開始値や調整パラメータに対して少し敏感である可能性があるため、Optim.jlで提供されるデフォルトに注意することが良いアイデアです。

勾配情報を使用する代わりに、Nelder-Meadは直接探索法です。探索空間内のいくつかの点で関数値を追跡します。これらの点は一緒に単体を形成します。単体が与えられた場合、反射、拡張、収縮、または縮小の4つのアクションのいずれかを実行できます。基本的に、目標は最悪の点をより良い点で反復的に置き換えることです。詳細については[1]、[2]、または[3]を参照してください。

## 参考文献

  * [1] Nelder, John A. and R. Mead (1965). "A simplex method for function minimization". Computer Journal 7: 308–313. doi:10.1093/comjnl/7.4.308
  * [2] Lagarias, Jeffrey C., et al. "Convergence properties of the Nelder–Mead simplex method in low dimensions." SIAM Journal on Optimization 9.1 (1998): 112-147
  * [3] Gao, Fuchang and Lixing Han (2010). "Implementing the Nelder-Mead simplex algorithm with adaptive parameters". Computational Optimization and Applications. doi:10.1007/s10589-010-9329-3
