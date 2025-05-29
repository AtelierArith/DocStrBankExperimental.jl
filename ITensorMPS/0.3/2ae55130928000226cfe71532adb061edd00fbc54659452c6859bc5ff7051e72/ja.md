```
expand(state::MPS, reference::MPO; alg="global_krylov", krylovdim=2, cutoff)
```

MPS `state` と MPO `reference` を与えると、`state` と等しい MPS を返します（`state` と忠実度 1 を持つ）が、MPS 基底が `state` の MPS 基底に直交する Krylov 空間の基底の一部を含むように拡張されます。`reference` 演算子は `state` に `krylovdim` 回適用され、デフォルトは 2 で、信頼性とパフォーマンスの良いバランスを提供します。詳細については [^global_expansion] を参照してください。

カットオフは拡張された基底の切り捨てを制御するために使用され、デフォルトは入力状態のスカラー型の精度の半分、すなわち `Float64` の場合は約 1e-8 です。

!!! warning
    ユーザーには、拡張の効果とさまざまなシナリオでのパフォーマンスの間の適切なバランスについての経験を積むにつれて、あまり多くのカスタマイズオプションが提供されていません。デフォルト値やキーワード引数は、メソッドの最適な使用方法について学ぶにつれて変更される可能性があります。


[^global_expansion]: 時間依存変分原理と付随する Krylov 部分空間。Mingru Yang, Steven R. White, [arXiv:2005.06104](https://arxiv.org/abs/2005.06104)
