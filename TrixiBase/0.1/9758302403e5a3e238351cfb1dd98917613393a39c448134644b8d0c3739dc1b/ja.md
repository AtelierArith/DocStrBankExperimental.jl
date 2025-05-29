```
trixi_include([mapexpr::Function=identity,] [mod::Module=Main,] elixir::AbstractString; kwargs...)
```

`include` 関数を使用してファイル `elixir` を読み込み、その内容をモジュール `mod` のグローバルスコープで評価します。特定の代入を上書きするには、キーワード引数を指定します。この基本的な目的は、REPLからシミュレーションを実行する際に、いくつかのパラメータを簡単に変更できるようにすることです。さらに、これはテストで使用され、CIの計算負担を軽減しつつ、ユーザーにとって合理的なデフォルト値を持つ例を提供します。

`elixir` 内の代入を置き換える前に、キーワード引数 `maxiters` が `solve` への呼び出しに挿入され、そのデフォルト値はODEのためにSciMLエコシステムで使用されます。詳細は [documentation](https://docs.sciml.ai/DiffEqDocs/stable/basics/common_solver_opts/) の「Miscellaneous」セクションを参照してください。

オプションの最初の引数 `mapexpr` は、評価される前に含まれるコードを変換するために使用できます：`elixir` 内の各解析された式 `expr` に対して、`include` 関数は実際に `mapexpr(expr)` を評価します。省略した場合、`mapexpr` は `identity` にデフォルト設定されます。

# 例

```@example
julia> using TrixiBase, Trixi

julia> redirect_stdout(devnull) do
         trixi_include(@__MODULE__, joinpath(examples_dir(), "tree_1d_dgsem", "elixir_advection_extended.jl"),
                       tspan=(0.0, 0.1))
         sol.t[end]
       end
[ Info: You just called `trixi_include`. Julia may now compile the code, please be patient.
0.1
```
