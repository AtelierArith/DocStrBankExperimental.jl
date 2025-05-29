```
f = @define_with_derivatives(ex1, ex2, ex3)
```

新しい関数 f を宣言し、与えられた式を用いてその導関数が計算されるように、導関数に関連するさまざまな関数を再定義します。

# ```jldoctest

# julia> f = @define*with*derivatives x->x^2 x->2x x->2;

# ERROR: LoadError: UndefVarError: `@define_with_derivatives` not defined

# in expression starting at none:1

# julia> value*and*derivative(f, 45)

# ERROR: UndefVarError: `value_and_derivative` not defined

# Stacktrace:

# [1] top-level scope

# @ none:1

# ```

3つのマクロパラメータは、スペースで区切られていることに注意してください（カンマや括弧はありません）。

# ```jldoctest

# julia> g = @define*with*derivatives x->12 x->34 x->56;

# ERROR: LoadError: UndefVarError: `@define_with_derivatives` not defined

# in expression starting at none:1

# julia> value*derivative*and*second*derivative(g, -23.5)

# ERROR: UndefVarError: `value_derivative_and_second_derivative` not defined

# Stacktrace:

# [1] top-level scope

# @ none:1

# ```

これは便利のために提供されていますが、多くの場合、関数とその導関数の中に共通の部分式を見つけることができるため、2つの関数を別々に定義する方が効率的です。

この方法で導関数を定義する場合、間違い（例えば、因子2を忘れるなど）がないことを確認するために `check_derivatives` を実行することをお勧めします。自動的に実行しないのは、`f` の定義域内で有効な `x` を知る必要があるからです。
