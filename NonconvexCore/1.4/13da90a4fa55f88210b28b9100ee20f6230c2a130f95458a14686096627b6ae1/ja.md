```
optimize(
    model::AbstractModel,
    optimizer::AbstractOptimizer = MMA02(),
    x0::AbstractVector;
    options,
    convcriteria::ConvergenceCriteria = KKTCriteria(),
    plot_trace::Bool = false,
    callback::Function = plot_trace ? LazyPlottingCallback() : NoCallback(),
    kwargs...,
)

```

`model`を`optimizer`アルゴリズムを使用して最適化します。例えば、[`MMA87`](@ref)または[`MMA02`](@ref)のインスタンスです。`x0`は初期解です。キーワード引数は次のとおりです。

  * `options`: 最適化オプションを設定するために使用されます。これは[`MMAOptions`](@ref)のインスタンスであり、[`MMA87`](@ref)および[`MMA02`](@ref)用です。
  * `convcriteria`: MMAアルゴリズムの収束基準を指定する[`ConvergenceCriteria`](@ref)のインスタンスです。
  * `plot_trace`: 真の場合、コールバックを[`PlottingCallback`](@ref)のインスタンスに指定し、最後の50の解のライブトレースをプロットするブール値です。
  * `callback`: アルゴリズムの各イテレーションで`solution`に対して呼び出される関数です。これは最適化プロセスに関する情報を保存するために使用できます。

MMA最適化アルゴリズムの詳細は、元の[1987 MMA論文](https://onlinelibrary.wiley.com/doi/abs/10.1002/nme.1620240207)および[2002年の論文](https://epubs.siam.org/doi/abs/10.1137/S1052623499362822)で見つけることができます。
