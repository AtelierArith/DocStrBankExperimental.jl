```
jet_reconstruct(particles::AbstractVector; p::Union{Real, Nothing} = nothing,
                     algorithm::Union{JetAlgorithm.Algorithm, Nothing} = nothing,
                     R = 1.0, recombine = +,
                     strategy::RecoStrategy.Strategy = RecoStrategy.Best)
```

指定されたアルゴリズムと戦略を使用して、粒子のコレクションからジェットを再構築します。

# 引数

  * `particles::AbstractVector`: ジェット再構築に使用される粒子のコレクション。
  * `p::Union{Real, Nothing} = nothing`: 一般化された k_T の距離測定に使用されるパワー値で、特定の再構築アルゴリズムにマッピングされます（-1 = AntiKt、0 = Cambridge/Aachen、1 = Kt）。
  * `algorithm::Union{JetAlgorithm.Algorithm, Nothing} = nothing`: ジェット再構築に使用するアルゴリズム。
  * `R = 1.0`: ジェット半径パラメータ。
  * `recombine = +`: 粒子を結合するために使用される再結合スキーム。
  * `strategy::RecoStrategy.Strategy = RecoStrategy.Best`: 使用するジェット再構築戦略。`RecoStrategy.Best` は、開始粒子の数に基づいて動的な決定を行います。

`p` または `algorithm` のいずれかを指定する必要があり、`algorithm` が優先されます。

# 戻り値

再構築されたジェットとマージ履歴を含むクラスタシーケンスオブジェクト。

# 詳細

## `particles` 引数

`pt2()`, `phi()`, `rapidity()`, `px()`, `py()`, `pz()`, `energy()`（`JetReconstruction` 名前空間内）メソッドを提供する任意のタイプを使用できます。これには、`LorentzVector`、`LorentzVectorCyl`、および `PseudoJet` が含まれ、これらのメソッドはすでに `JetReconstruction` 名前空間内で定義されています。

## `recombine` 引数

`recombine` 引数は、粒子のペアをマージするために使用される関数です。デフォルトは単に `+(jet1,jet2)` であり、すなわち 4-モーメンタの加算または *E* スキームです。

## `p`、`algorithm` および `R` 引数の整合性

アルゴリズムが明示的に指定されている場合、`p` 値はそれと整合性があるか、`nothing` である必要があります。`p` が変動可能なアルゴリズムの場合、アルゴリズムとともに指定する必要があります。

`p` パラメータが渡され、`algorithm=nothing` の場合、ppタイプの再構築が暗示されます（すなわち、`p` の値に応じて AntiKt、CA、Kt または GenKt が使用されます）。

アルゴリズムに `R` 依存性がない場合、`R` パラメータは無視されます。

# 例

```julia
jet_reconstruct(particles; p = -1, R = 0.4)
jet_reconstruct(particles; algorithm = JetAlgorithm.Kt, R = 1.0)
jet_reconstruct(particles; algorithm = JetAlgorithm.Durham)
jet_reconstruct(particles; algorithm = JetAlgorithm.GenKt, p = 0.5, R = 1.0)
```
