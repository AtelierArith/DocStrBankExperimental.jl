```
minimax(r::Barycentric, f::Function, nsteps::Integer=20)
minimax(r::Approximation, nsteps::Integer=20)
```

与えられたバリセントリック形式の有理関数のノード上で関数 `f` に対する近似的なミニマックス有理近似を計算します。返される近似は最初の入力引数と同じ型になります。

`nsteps` 引数はローソン反復の回数を制御します。デフォルト値は 20 です。

# 例

```julia-repl
julia> f(x) = tanh( 40*(x - 0.15) );

julia> r = approximate(f, unit_interval, max_degree=8);  # 最小二乗近似

julia> check(r);
[ Info: 最大誤差は 1.06e-02 です

julia> r̂ = minimax(r);

julia> check(r̂);
[ Info: 最大誤差は 1.40e-03 です
```
