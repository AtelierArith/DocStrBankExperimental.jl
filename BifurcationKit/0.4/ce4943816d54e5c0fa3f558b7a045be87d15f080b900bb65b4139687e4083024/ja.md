```julia
struct BifurcationProblem{Tvf, Tu, Tp, Tl<:Union{typeof(identity), Accessors.IndexLens, Accessors.PropertyLens, ComposedFunction}, Tplot, Trec, Tgets, Tupdate} <: BifurcationKit.AbstractAllJetBifProblem
```

バイフルケーション問題を保持するための構造体です。

## フィールド

  * `VF::Any`: ベクトル場、通常は [`BifFunction`](@ref)
  * `u0::Any`: 初期推測
  * `params::Any`: パラメータ
  * `lens::Union{typeof(identity), Accessors.IndexLens, Accessors.PropertyLens, ComposedFunction}`: 通常は `Accessors.PropertyLens`。これは、継続に使用される `params` のどのパラメータ軸が指定されているかを示します。例えば、`par = (α = 1.0, β = 1)` の場合、`lens = (@optic _.α)` を使用することで `α` に関して継続を行うことができます。配列 `par = [ 1.0, 2.0]` があり、最初の変数に関して継続を行いたい場合は、`lens = (@optic _[1])` を使用できます。詳細については `Accessors.jl` を参照してください。
  * `plotSolution::Any`: 継続中に解をプロットするためのユーザー関数。シグネチャ: `plot_solution(x, p; kwargs...)` は Plot.jl 用、`plot_solution(ax, x, p; ax1 = nothing, kwargs...)` は Makie パッケージ用です。
  * `recordFromSolution::Any`: 解に関するいくつかの指標を記録するために使用される `record_from_solution = (x, p; k...) -> norm(x)` 関数。これは `norm` または `(x, p; k...) -> x[1]` である可能性があります。これは、メモリの理由からいくつかの巨大なベクトルを保存することができない場合にも便利です（例えば、GPU上で）。この関数はほぼすべてのものを返すことができますが、小さく保つべきです。例えば、`(x, p; k...) -> (x1 = x[1], x2 = x[2], nrm = norm(x))` または単に `(x, p; k...) -> (sum(x), 1)` を行うことができます。これは `contres.branch` に保存され、ここで `contres::ContResult` はバイフルケーション問題の継続曲線です。最後に、最初のコンポーネントは継続曲線のプロットに使用されます。
  * `save_solution::Any`: ブランチ上の完全な解を保存するための関数。一部の問題は可変であり（適応メッシュを持つ周期軌道機能のように）、この関数は解自体とともに問題の状態を保存することを可能にします。出力を割り当てる必要があることに注意してください（`x` へのビューではなく）。シグネチャ: `save_solution(x, p)`
  * `update!::Any`: 各継続ステップの後に問題を更新するために使用される関数

## メソッド

  * `re_make(pb; kwargs...)` バイフルケーション問題を修正します
  * `getu0(pb)` `pb.u0` を呼び出します
  * `getparams(pb)` `pb.params` を呼び出します
  * `getlens(pb)` `pb.lens` を呼び出します
  * `getparam(pb)` `get(pb.params, pb.lens)` を呼び出します
  * `setparam(pb, p0)` `set(pb.params, pb.lens, p0)` を呼び出します
  * `record_from_solution(pb)` `pb.recordFromSolution` を呼び出します
  * `plot_solution(pb)` `pb.plotSolution` を呼び出します
  * `is_symmetric(pb)` `is_symmetric(pb.prob)` を呼び出します

## コンストラクタ

  * `BifurcationProblem(F, u0, params, lens)` すべての導関数は ForwardDiff を使用して計算されます。
  * `BifurcationProblem(F, u0, params, lens; J, Jᵗ, d2F, d3F, kwargs...)` および `kwargs` は上記のフィールドです。`J` を使用して独自のヤコビアンを渡すことができ（ヤコビアン関数の説明については [`BifFunction`](@ref) を参照）、`Jᵗ` でヤコビアンの随伴を渡すことができます。例えば、これは `BifurcationKit.finite_differences` を使用して有限差分に基づくヤコビアンを提供するために使用できます。また、次のものを渡すこともできます。

      * `record_from_solution` 上記を参照
      * `plot_solution` 上記を参照
      * `issymmetric[=false]` ヤコビアンが対称であるかどうか、これにより随伴を提供する必要がなくなります
      * `jvp` ヤコビアン-ベクトル積、シグネチャ `jvp(x,p,dx)`
      * `vjp` ベクトル-ヤコビアン積（jvp の随伴）、シグネチャ `vjp(x,p,dx)`
      * `d2F` `x` に関する `F` の第二微分、シグネチャ `d2F(x,p,dx1,dx2)`
      * `d3F` `x` に関する `F` の第三微分、シグネチャ `d3F(x,p,dx1,dx2,dx3)`
      * `save_solution` `br.sol` に書き込まれる解を記録する特定の方法を指定します。これは非常に特定の状況で便利であり、代わりに `record_from_solution` を使用することをお勧めします。例えば、これはコレクション法でメッシュを記録するために内部的に使用されます。このメッシュは変更される可能性があります。
