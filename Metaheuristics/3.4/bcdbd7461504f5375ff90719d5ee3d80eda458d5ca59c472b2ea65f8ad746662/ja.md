```
set_user_solutions!(optimizer, x, fx;verbose=true)
```

`optimizer`に初期解を提供します。

  * `x`は`Vector`であり、`fx`は関数または`fx = f(x)`であることができます。
  * `x`は行に解を含む行列であることもできます。

### 例

```julia-repl
julia> f(x) = abs(x[1]) + x[2]  + x[3]^2 # 目的関数
f (generic function with 1 method)

julia> algo  = ECA(N = 61); # 最適化アルゴリズム

julia> # 一つの解を提供できます
       x0 = [0.5, 0.5, 0.5];

julia> set_user_solutions!(algo, x0, f);

julia> # 複数の解を提供する
       X0 = rand(30, 3); # 次元3の30の解

julia> set_user_solutions!(algo, X0, f);

julia> optimize(f, [0 0 0; 1 1 1.0], algo)
+=========== RESULT ==========+
  iteration: 413
    minimum: 0
  minimizer: [0.0, 0.0, 0.0]
    f calls: 25132
 total time: 0.0856 s
stop reason: 目的関数の値の小さな差。
+============================+
```
