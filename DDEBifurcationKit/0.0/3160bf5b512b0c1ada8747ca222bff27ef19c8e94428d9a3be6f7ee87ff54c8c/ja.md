```julia
struct ConstantDDEBifProblem{Tvf, Tdf, Tu, Td, Tp, Tl<:Union{typeof(identity), Nothing, Accessors.IndexLens, Accessors.PropertyLens, ComposedFunction}, Tplot, Trec, Tgets, Tδ} <: DDEBifurcationKit.AbstractDDEBifurcationProblem
```

バイフルケーション問題を保持するための構造体。パラメータがない場合は、`nothing`を渡すことができます。

## フィールド

  * `VF::Any`: ベクトル場、通常は[`BifFunction`](@ref)です。詳細については、ウェブサイト https://bifurcationkit.github.io/DDEBifurcationKit.jl/dev/BifProblem をご覧ください。
  * `delays::Any`: 関数の遅延。パラメータを受け取り、`AbstractVector`形式で非ゼロの遅延を返します。例: `delays = par -> [1.]`
  * `u0::Any`: 初期推測
  * `delays0::Any`: 初期遅延（コンストラクタによって内部的に設定されます）
  * `params::Any`: パラメータ
  * `lens::Union{typeof(identity), Nothing, Accessors.IndexLens, Accessors.PropertyLens, ComposedFunction}`: 通常は`Accessors.@optic`です。`params`の中でどのパラメータ軸が連続性に使用されるかを指定します。例えば、`par = (α = 1.0, β = 1)`の場合、`lens = (@optic _.α)`を使用することで`α`に関して連続性を実行できます。配列`par = [ 1.0, 2.0]`があり、最初の変数に関して連続性を実行したい場合は、`lens = (@optic _[1])`を使用できます。詳細については、`Accessors.jl`を参照してください。
  * `plotSolution::Any`: 連続性の間に解をプロットするためのユーザー関数。シグネチャ: `plotSolution(x, p; kwargs...)`
  * `recordFromSolution::Any`: `record_from_solution = (x, p; k...) -> norm(x)`関数は、解に関するいくつかの指標を記録するために使用されます。これは`norm`や`(x, p) -> x[1]`である可能性があります。これは、メモリの理由（例えばGPU上で）でいくつかの巨大なベクトルを保存することができない場合にも便利です。この関数はほぼすべてを返すことができますが、小さく保つべきです。例えば、`(x, p) -> (x1 = x[1], x2 = x[2], nrm = norm(x))`や単に`(x, p) -> (sum(x), 1)`を行うことができます。これは`contres.branch`に保存されます（下記参照）。最後に、最初のコンポーネントは連続曲線にプロットするために使用されます。
  * `save_solution::Any`: ブランチ上の完全な解を保存するための関数。一部の問題は可変（適応メッシュを持つ周期軌道関数のように）であり、この関数は解自体とともに問題の状態を保存することを可能にします。シグネチャ `save_solution(x, p)`
  * `δ::Any`: 有限差分のためのデルタ

## メソッド

  * `getu0(pb)` は `pb.u0` を呼び出します
  * `getparams(pb)` は `pb.params` を呼び出します
  * `getlens(pb)` は `pb.lens` を呼び出します
  * `setparam(pb, p0)` は `set(pb.params, pb.lens, p0)` を呼び出します
  * `record_from_solution(pb)` は `pb.record_from_solution` を呼び出します

## コンストラクタ

  * `ConstantDDEBifProblem(F, delays, u0, params, lens; J, Jᵗ, d2F, d3F, kwargs...)` と `kwargs` は上記のフィールドです。
