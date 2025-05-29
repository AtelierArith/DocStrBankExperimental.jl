```
DouglasRachford(M, f, proxes_f, p)
DouglasRachford(M, mpo, p)
DouglasRachford!(M, f, proxes_f, p)
DouglasRachford!(M, mpo, p)
```

マニフォールド $\mathcal M$ 上でのダグラス-ラチフォードアルゴリズムを、与えられた（2つの）近接写像 `proxes_f` を用いて `p` から開始して計算します。詳細は [BergmannPerschSteidl:2016](@cite) を参照してください。

$$
k>2
$$

の近接写像の場合、問題は並列ダグラス-ラチフォードを用いて再定式化されます：ベクトル型の近接写像が冪マニフォールド $\mathcal M^k$ 上に導入され、最初の近接写像が設定され、2番目の近接写像は [`mean`](@extref Statistics.mean-Tuple{AbstractManifold, Vararg{Any}})（リーマン中心）に設定されます。したがって、これは2つの近接写像に還元されますが、各近接写像は並列に、すなわちベクトル内の成分ごとに評価されます。

!!! note



現在のところ、並列ダグラス-ラチフォードはインプレースで動作しません。なぜなら、冪マニフォールド上に新しい開始点 `p'` を作成する際に、`p` のコピーが作成されるからです。

代わりに [`ManifoldProximalMapObjective`](@ref) `mpo` を提供すると、近接写像は変更されません。

# 入力

  * `M::`[`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`)``: リーマン多様体 $\mathcal M$
  * `f`: コスト関数 $f: \mathcal M→ ℝ$ を `(M, p) -> v` として実装
  * `proxes_f`: 近接写像を実行する形式 `(M, λ, p)-> q` の関数で、ここで `⁠λ` は各 `F` の和の近接パラメータを示します。これらは [`InplaceEvaluation`](@ref) の変種 `(M, q, λ p) -> q` で与えることもでき、`q` のインプレース計算を行います。
  * `p`: マニフォールド $\mathcal M$ 上の点

# キーワード引数

  * `α= k -> 0.9`: 古い反復から新しい反復へのステップの緩和、正確には $p^{(k+1)} = g(α_k; p^{(k)}, q^{(k)})$ で、ここで $q^{(k)}$ は DR アルゴリズムに関与する二重反射の結果であり、$g$ は引き戻しとその逆によって誘導される曲線です。
  * `evaluation=`[`AllocatingEvaluation`](@ref)`()`: 配列を返す関数、例えば点や接ベクトルが、その結果を割り当てることで動作するか（[`AllocatingEvaluation`](@ref)）、または入力引数を修正してその中で結果を返すか（[`InplaceEvaluation`](@ref））を指定します。通常、最初の引数はマニフォールドであり、修正された引数は2番目になります。
  * `inverse_retraction_method=`[`default_inverse_retraction_method`](@extref `ManifoldsBase.default_inverse_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用する逆引き戻し $\operatorname{retr}^{-1}$、詳細は [引き戻しとその逆に関するセクション](@extref ManifoldsBase :doc:`retractions`) を参照してください。これは緩和ステップと反射の両方で使用されますが、`R` を自分で設定しない限り。
  * `λ= k -> 1.0`: 近接パラメータ $λ_k$ の値を提供する関数
  * `R=reflect(!)`: 反復中に `p` の近接点での反射を実行するために使用されるメソッド。これはデフォルトで [`reflect`](@ref) または `reflect!` を使用し、`reflection_evaluation` と `retraction_method` および `inverse_retraction_method` で指定された引き戻しと逆引き戻しに依存します。
  * `reflection_evaluation`: （[`AllocatingEvaluation`](@ref) `R` がインプレースで動作するか割り当てるか
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用する引き戻し $\operatorname{retr}$、詳細は [引き戻しに関するセクション](@extref ManifoldsBase :doc:`retractions`) を参照してください。これは緩和ステップと反射の両方で使用されますが、`R` を自分で設定しない限り。
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(200)`[`|`](@ref StopWhenAny)[`StopWhenChangeLess`](@ref)`(1e-5)`: 停止基準が満たされていることを示すファンクタ
  * `parallel=false`: 並列ダグラス-ラチフォードを使用するかどうかを示します。

他のすべてのキーワード引数は、状態デコレーター用の [`decorate_state!`](@ref) または目的デコレーター用の [`decorate_objective!`](@ref) に渡されます。

# 出力

得られた近似最小化点 $p^*$。ソルバーの全体的な最終状態を取得するには、特に `return_state=` キーワードについては [`get_solver_return`](@ref) を参照してください。 ```
