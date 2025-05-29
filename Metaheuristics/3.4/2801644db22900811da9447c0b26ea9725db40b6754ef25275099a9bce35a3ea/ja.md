```
MOEAD_DE(weights ;
    F = 0.5,
    CR = 1.0,
    λ = Array{Vector{Float64}}[], # 参照点
    η = 20,
    p_m = -1.0,
    T = round(Int, 0.2*length(weights)),
    δ = 0.9,
    n_r = round(Int, 0.02*length(weights)),
    z = zeros(0),
    B = Array{Int}[],
    s1 = 0.01,
    s2 = 20.0,
    information = Information(),
    options = Options())
```

`MOEAD_DE`は、MOEA/D-DEのオリジナルバージョンを実装しています。これは、違反の合計に基づく制約処理方法を使用します（制約最適化用）：`g(x, λ, z) = max(λ .* abs.(fx - z)) + sum(max.(0, gx)) + sum(abs.(hx))`

`MOEAD_DE`を使用するには、目的関数からの出力が3つ組 `(f::Vector, g::Vector, h::Vector)` である必要があります。ここで、`f`は目的関数を含み、`g`と`h`はそれぞれ等式制約と不等式制約です。

実行可能な解は、`g_i(x) ≤ 0` および `h_j(x) = 0` であるようなものです。

参考文献: 複雑なパレート集合を持つ多目的最適化問題、MOEA/DおよびNSGA-II; Hui LiおよびQingfu Zhang。

# 例

次の最適化問題を解決したいと仮定します：

最小化：

`f(x) = (x_1, x_2)`

制約条件：

`g(x) = x_1^2 + x_2^2 - 1 ≤ 0`

`x_1, x_2 ∈ [-1, 1]`

解は次のようになります：

```julia

# 次元
D = 2

# 目的関数
f(x) = ( x, [sum(x.^2) - 1], [0.0] )

# 範囲
bounds = [-1 -1;
           1  1.0
        ]

nobjectives = 2
npartitions = 100

# 参照点（DasとDennisの方法）
weights = gen_ref_dirs(nobjectives, npartitions)

# パラメータを定義
moead_de = MOEAD_DE(weights, options=Options(debug=false, iterations = 250))

# 最適化
status_moead = optimize(f, bounds, moead_de)

# 結果を表示
display(status_moead)
```
