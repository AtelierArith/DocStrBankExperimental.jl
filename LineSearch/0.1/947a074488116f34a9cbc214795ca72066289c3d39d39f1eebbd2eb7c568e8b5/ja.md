```
LineSearchesJL(; method = LineSearches.Static(), autodiff = nothing,
    initial_alpha = true)
```

[LineSearches.jl](https://github.com/JuliaNLSolvers/LineSearches.jl/)のアルゴリズムをラップします。自動微分を利用して、ラインサーチアルゴリズムの目的関数を自動的に構築し、高速なVJPまたはJVPを実現します。

!!! warning
    この機能を使用する前に、`LineSearches.jl`を明示的にロードする必要があります。


### 引数

  * `method`: 使用するラインサーチアルゴリズム。デフォルトは`method = LineSearches.Static()`で、これはステップサイズが`alpha`の値に固定されることを意味します。
  * `autodiff`: ラインサーチに使用する自動微分バックエンド。解析的ヤコビアン/JVP/VJPが利用できない場合は指定する必要があります。
  * `initial_alpha`: 使用する初期ステップサイズ。デフォルトは`true`（これは`1`に相当します）。
