```
check_derivatives(f, x=rand())
```

関数 f の導関数が、TaylorSeries によって計算されたものと一致するか（マシン精度の平方根まで）を確認します（アサーションを使用）。

これは、導関数を再定義する場合の有用なサニティチェックです。

導関数は、`f` の定義域にある点 `x`（デフォルト: rand()）でチェックされます。

# ```jldoctest

# julia> f = @define*with*derivatives x->x^2 x->2x x->2;

# ERROR: LoadError: UndefVarError: `@define_with_derivatives` not defined

# in expression starting at none:1

# julia> check_derivatives(f, 0.2)

# ERROR: UndefVarError: `check_derivatives` not defined

# Stacktrace:

# [1] top-level scope

# @ none:1

# julia> g = @define*with*derivatives x->x^2 x->2x x->3;

# ERROR: LoadError: UndefVarError: `@define_with_derivatives` not defined

# in expression starting at none:1

# julia> check_derivatives(g, 0.2)

# ERROR: UndefVarError: `check_derivatives` not defined

# Stacktrace:

# [1] top-level scope

# @ none:1

# ```
