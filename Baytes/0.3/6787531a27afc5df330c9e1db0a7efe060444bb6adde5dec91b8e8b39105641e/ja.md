```julia
construct(
    _rng,
    model,
    data,
    default,
    tempering,
    datatune,
    chains,
    updatesampler,
    args
)

```

`chains` MCMCチェーンを構築し、`args`に記載されたすべてのアルゴリズムを個別に開始します。ポインタの問題を避けるために、各チェーンに対して別々のモデルが提供されます。`args`が単一の`SMC`アルゴリズムである場合、チェーンは個別に割り当てられず、代わりにアルゴリズム内で使用されます。他のmcmcサンプラーと一緒に`args`で使用される場合でも、smcは意図した通りに機能することに注意してください。

# 例

```julia

```
