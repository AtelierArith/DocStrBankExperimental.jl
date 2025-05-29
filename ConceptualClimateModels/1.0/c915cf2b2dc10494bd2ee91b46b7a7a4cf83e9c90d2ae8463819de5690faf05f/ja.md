```
plausible_ic_sampler(ds::DynamicalSystem [, seed])
```

`sampler`を返します。これは0引数関数`sampler()`として呼び出すことができ、`ds`の[`plausible_limits`](@ref)によって定義されたハイパーレクタングル内のランダムな初期条件を生成します。`sampler`は、例えば`DynamicalSystems.basins_fractions`に渡すのに便利です。
