```
solve!(solver::AbstractLinearSolver, b; x0 = 0, callbacks = (_, _) -> nothing)
```

データベクトル `b` に対して `solver` を使用して逆問題を解きます。

# 必要な引数

  * `solver::AbstractLinearSolver`    - 線形ソルバー（例：`ADMM` または `FISTA`）、前方/通常演算子と正則化子を含む
  * `b::AbstractVector`               - ソルバーに `A` が供給された場合のデータベクトル、そうでない場合はデータの逆投影

# オプションのキーワード引数

  * `x0::AbstractVector`              - 解の初期推定；デフォルトはゼロ
  * `callbacks`              - （オプションでベクトルの）関数または呼び出し可能な構造体で、2つの引数 `callback(solver, iteration)` を受け取り、例えば中間解や収束パラメータを保存、印刷、またはプロットします。コールバック関数内で `solver` や `iteration` を変更しないようにしてください。そうしないと収束が妨げられます。デフォルトは何もしません。

# 例

最適化問題

$$
	argmin_x ||Ax - b||_2^2 + λ ||x||_1
$$

は、以下のコード行で解くことができます：

```jldoctest solveExample
julia> using RegularizedLeastSquares

julia> A = [0.831658  0.96717
            0.383056  0.39043
            0.820692  0.08118];

julia> x = [0.5932234523399985; 0.2697534345340015];

julia> b = A * x;

julia> S = ADMM(A, reg = L1Regularization(0.0001));

julia> x_approx = solve!(S, b)
2-element Vector{Float64}:
 0.5932171509222105
 0.26971370566079866
```

ここでは、[`L1Regularization`](@ref) を使用しています。すべての正則化オプションは [API for Regularizers](@ref) で見つけることができます。

次の例は、同じ問題を解きますが、各イテレーションの解 `x` を `tr` に保存します：

```jldoctest solveExample
julia> tr = Dict[]
Dict[]

julia> store_trace!(tr, solver, iteration) = push!(tr, Dict("iteration" => iteration, "x" => solver.x, "beta" => solver.β))
store_trace! (generic function with 1 method)

julia> x_approx = solve!(S, b; callbacks=(solver, iteration) -> store_trace!(tr, solver, iteration))
2-element Vector{Float64}:
 0.5932234523399984
 0.26975343453400163

julia> tr[3]
Dict{String, Any} with 3 entries:
  "iteration" => 2
  "x"         => [0.593223, 0.269753]
  "beta"      => [1.23152, 0.927611]
```

最後の例は、10回ごとに解をプロットし、ソルバーの収束メトリクスを保存する方法を示しています：

```julia
julia> using Plots

julia> conv = StoreConvergenceCallback()

julia> function plot_trace(solver, iteration)
         if iteration % 10 == 0
           display(scatter(solver.x))
         end
       end
plot_trace (generic function with 1 method)

julia> x_approx = solve!(S, b; callbacks = [conv, plot_trace]);
```

キーワード `callbacks` を使用すると、引数 `solver` と `iteration` を受け取り、中間結果を印刷、保存、またはプロットする（ベクトルの）呼び出し可能なオブジェクトを渡すことができます。

他にも、[`StoreSolutionCallback`](@ref)、[`StoreConvergenceCallback`](@ref)、[`CompareSolutionCallback`](@ref) など、提供されているコールバックオプションがいくつかあります。
