```
expand(state::MPS, references::Vector{MPS}; alg="orthogonalize", cutoff)
```

与えられたMPS `state`とMPS `references`のコレクションに対して、`state`と等しいMPS（`state`との忠実度が1である）を返しますが、そのMPS基底は`state`のMPS基底に直交する`references`の基底の一部を含むように拡張されています。詳細については [^global_expansion] を参照してください。

カットオフは拡張された基底の切り捨てを制御するために使用され、デフォルトでは入力状態のスカラー型の精度の半分、すなわち`Float64`の場合は約1e-8です。

!!! warning
    ユーザーには、拡張の効果とさまざまなシナリオでのパフォーマンスの間の適切なバランスについての経験を積むにつれて、まだ多くのカスタマイズオプションが提供されていません。デフォルト値やキーワード引数は、メソッドの最適な使用方法についての理解が深まるにつれて変更される可能性があります。


[^global_expansion]: 時間依存変分原理と付随するクリロフ部分空間。Mingru Yang, Steven R. White, [arXiv:2005.06104](https://arxiv.org/abs/2005.06104)
