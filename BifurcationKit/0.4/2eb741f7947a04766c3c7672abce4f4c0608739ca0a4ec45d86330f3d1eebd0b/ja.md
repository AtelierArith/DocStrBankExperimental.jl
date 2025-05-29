```julia
struct ContResult{Tkind<:BifurcationKit.AbstractContinuationKind, Tbr, Teigvals, Teigvec, Biftype, Tsol, Tparc, Tprob, Talg} <: BifurcationKit.AbstractResult{Tkind<:BifurcationKit.AbstractContinuationKind, Tprob}
```

[`continuation`](@ref)への呼び出し後の結果を保持する構造体です。

結果 `br` のプロパティ名は、`propertynames(br)` または `propertynames(br.branch)` を使用することで確認できます。

# フィールド

  * `branch::StructArrays.StructArray`: ブランチに関する低次元の情報を保持します。より正確には、`branch[i+1]` には各継続ステップ `i` に対して次の情報が含まれます `(record_from_solution(u, param), param, itnewton, itlinear, ds, θ, n_unstable, n_imag, stable, step)`。

      * `itnewton` ニュートン反復の回数
      * `itlinear` ニュートン（補正器）中の線形反復の総数
      * `n_unstable` 各継続ステップにおける正の実部を持つ固有値の数（定常分岐を検出するため）
      * `n_imag` 現在の継続ステップにおける正の実部と非ゼロの虚部を持つ固有値の数（ホップ分岐を検出するのに便利）。
      * `stable` 各継続ステップに対して計算された解の安定性。したがって、`stable` は与えられた `k` に対する `branch[k]` に対応する `eig[step]` と一致する必要があります。
      * `step` 継続ステップ（ここでは `i` に等しい）
  * `eig::Array{@NamedTuple{eigenvals::Teigvals, eigenvecs::Teigvec, converged::Bool, step::Int64}, 1} where {Teigvals, Teigvec}`: 各継続ステップにおける固有要素を持つベクトル。
  * `sol::Any`: ブランチに沿ってサンプリングされた解のベクトル。これは [`ContinuationPar`](@ref) の引数 `save_sol_every_step::Int64`（デフォルトは 0）によって設定されます。
  * `contparams::Any`: このブランチを生成するために `continuation` に渡されたパラメータ。`[`ContinuationPar`](@ref)` である必要があります。
  * `kind::BifurcationKit.AbstractContinuationKind`: このブランチで計算された解のタイプ。デフォルト: EquilibriumCont()
  * `prob::Any`: ブランチを計算するために使用された分岐問題。ブランチスイッチングに便利です。たとえば、周期軌道を計算する際に、関数 `PeriodicOrbitTrapProblem`、`ShootingProblem`... がここに保存されます。デフォルト: なし
  * `specialpoint::Vector`: 検出された分岐点のリストを保持するベクトル。特別な点のリストについては [`SpecialPoint`](@ref) を参照してください。
  * `alg::Any`: ブランチの計算に使用された継続アルゴリズム

# 関連メソッド

  * `length(br)` 継続ステップの数
  * `show(br)` ブランチに関する情報を表示
  * `propertynames(br)` 結果のプロパティ名を提供
  * `eigenvals(br, ind)` ind-th 継続ステップの固有値を返す
  * `eigenvec(br, ind, indev)` ind-th 継続ステップのindev-th 固有ベクトルを返す
  * `get_normal_form(br, ind)` `br.specialpoint` の ind-th ポイントの正規形を計算
  * `getlens(br)` ブランチに使用されるパラメータ軸を返す
  * `getlenses(br)` 2つのパラメータの継続が使用される場合のブランチに使用されるパラメータ2軸を返す（Fold, Hopf, NS, PD）
  * `get_solx(br, k)` ブランチ上の k-th 解を返す
  * `get_solp(br, k)` ブランチ上の k-th 解に関連付けられたパラメータ値を返す
  * `getparams(br)` 継続に渡され、方程式 `F(x, par) = 0` で使用されるパラメータ。
  * `getparams(br, ind)` 継続に渡され、方程式 `F(x, par) = 0` で使用されるパラメータ（ind-th 継続ステップの場合）。
  * `setparam(br, p0)` 問題 `br.prob` のパラメータに対して `::Lens` に従ってパラメータ値 `p0` を設定
  * `getlens(br)` ブランチの計算に使用されたレンズを取得
  * `eigenvals(br, ind)` 継続ステップ `ind` の固有値を提供
  * `eigenvalsfrombif(br, ind)` 分岐点インデックス `ind` の固有値を提供
  * `type(br, ind)` ind-th 分岐点のタイプを返す
  * `br[k+1]` k-th ステップに関する情報を提供します。典型的な実行は次のようになります。

```
julia> br[1]
(x = 0.0, param = 0.1, itnewton = 0, itlinear = 0, ds = -0.01, θ = 0.5, n_unstable = 2, n_imag = 2, stable = false, step = 0, eigenvals = ComplexF64[0.1 - 1.0im, 0.1 + 1.0im], eigenvecs = ComplexF64[0.7071067811865475 - 0.0im 0.7071067811865475 + 0.0im; 0.0 + 0.7071067811865475im 0.0 - 0.7071067811865475im])
```

これは、現在のポイントのパラメータの値 `param`、その安定性、ニュートン反復に関する情報などを提供します。フィールドは `propertynames(br.branch)` を使用して取得できます。この情報は `br.branch` に保存されており、これは `StructArray` です。したがって、ブランチに沿ったパラメータのベクトルを次のように抽出できます。

```
julia> br.param
10-element Vector{Float64}:
 0.1
 0.08585786437626905
 0.06464466094067263
 0.03282485578727799
-1.2623798512809007e-5
-0.07160718539365075
-0.17899902778635765
-0.3204203840236672
-0.4618417402609767
-0.5
```

  * `continuation(br, ind)` ind-th 分岐点から自動ブランチスイッチング（aBS）を実行します。通常、平衡から平衡、または周期軌道から周期軌道への分岐です。
  * `continuation(br, ind, lens2)` ind-th 分岐点の2つのパラメータ `(getlens(br), lens2)` の継続を実行します。
  * `continuation(br, ind, probPO::AbstractPeriodicOrbitProblem)` ind-th 分岐点（ホップ分岐点である必要があります）から周期軌道のブランチへの aBS を実行します。

```
