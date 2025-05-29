```
(trace::U, weight) = generate(gen_fn::GenerativeFunction{T,U}, args::Tuple)
```

生成関数のトレースを返します。

```
(trace::U, weight) = generate(gen_fn::GenerativeFunction{T,U}, args::Tuple,
                                constraints::ChoiceMap)
```

与えられたランダムな選択に関する制約と一致する生成関数のトレースを返します。

引数 $x$ (`args`) と割り当て $u$ (`constraints`)（最初の形式では空です）を考慮して、$t \sim q(\cdot; u, x)$ をサンプリングし、$r \sim q(\cdot; x, t)$ をサンプリングし、トレース $(x, r, t)$ (`trace`) を返します。また、重み (`weight`) も返します：

$$
\log \frac{p(r, t; x)}{q(t; u, x) q(r; x, t)}
$$

`gen_fn` にオプションの末尾引数がある場合（すなわち、デフォルト値が提供されている場合）、オプション引数は `args` タプルから省略できます。生成されたトレースにはデフォルト値が埋め込まれます。

制約なしの例：

```julia
(trace, weight) = generate(foo, (2, 4))
```

`:z` が `true` の値を取るという制約のある例。

```julia
(trace, weight) = generate(foo, (2, 4), choicemap((:z, true))
```
