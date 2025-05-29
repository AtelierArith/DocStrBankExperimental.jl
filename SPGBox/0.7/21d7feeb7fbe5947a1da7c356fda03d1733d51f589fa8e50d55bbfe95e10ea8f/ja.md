```
Vaux(x, fx; m=10)
```

最適化アルゴリズムのための補助変数を格納する構造体です。

現在の点 `x` と、目的関数の出力と同じ型の値 `fx` で初期化する必要があります。

オプションで、保存する以前の関数値の数を `m` キーワード引数で設定できます。

# 例

```jldoctest
julia> using SPGBox

julia> f(x) = x[1]^2 + x[2]^2 + 1;

julia> g!(g,x) = g .= 2 .* x;

julia> x0 = [5.0, 3.0];

julia> vaux = SPGBox.VAux(x0, 0.0; m=5);

julia> spgbox!(f, g!, x0; vaux=vaux)

 SPGBOX RESULT: 

 Convergence achieved. 

 Final objective function value = 1.0
 Sample of best point = Vector{Float64}[ 0.0, 0.0]
 Projected gradient norm = 0.0

 Number of iterations = 3
 Number of function evaluations = 3
```
