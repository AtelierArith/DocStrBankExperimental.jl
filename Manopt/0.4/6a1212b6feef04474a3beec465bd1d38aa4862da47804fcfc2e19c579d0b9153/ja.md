```
DouglasRachford(M, f, proxes_f, p)
DouglasRachford(M, mpo, p)
```

マニフォールド $\mathcal M$ 上でダグラス・ラチフォードアルゴリズムを計算し、初期データ $p$ と（2つの）近接マップ `proxMaps` を使用します。詳細は [ BergmannPerschSteidl:2016](@cite) を参照してください。

$$
k>2
$$

の近接マップの場合、問題は平行ダグラス・ラチフォードを使用して再定式化されます：ベクトル近接マップがパワーマニフォールド $\mathcal M^k$ 上に導入され、最初の近接マップとして設定され、2番目の近接マップは `mean`（リーマン中心）に設定されます。したがって、これは2つの近接マップに還元されますが、それぞれは並行して近接マップを評価します。つまり、ベクトル内の成分ごとに評価されます。

代わりに [`ManifoldProximalMapObjective`](@ref) `mpo` を提供すると、近接マップは変更されません。

# 入力

  * `M`:        リーマン多様体 $\mathcal M$
  * `F`:        コスト関数の合計からなるコスト関数
  * `proxes_f`: 形式 `(M, λ, p)-> q` の関数で、近接マップを実行します。ここで `⁠λ` は近接パラメータを示し、$F$ の各和項に対して適用されます。これらは [`InplaceEvaluation`](@ref) バリアント `(M, q, λ p) -> q` で、`q` のインプレース計算としても与えることができます。
  * `p`:        初期データ $p ∈ \mathcal M$

# オプション値

  * `evaluation`:            ([`AllocatingEvaluation`](@ref)) 近接マップがアロケーション（デフォルト）形式 `prox(M, λ, x)` で動作するか、または [`InplaceEvaluation`](@ref) インプレースで動作するかを指定します
  * `λ`:                     (`(iter) -> 1.0`) 呼び出し中の近接パラメータの値を提供する関数
  * `α`:                     (`(iter) -> 0.9`) 古い反復から新しい反復へのステップの緩和、正確には $t_{k+1} = g(α_k; t_k, s_k)$ で、ここで $s_k$ は DR アルゴリズムに関与する二重反射の結果です
  * `inverse_retraction_method` - (`default_inverse_retraction_method(M, typeof(p))`) 使用する逆引き戻し

      * 反射（`R` を直接設定した場合は無視されます）
      * 緩和ステップ
  * `R`:                     近接 `p` での `x` の反射を実行するために反復で使用されるメソッド。これはデフォルトで [`reflect`](@ref) または `reflect!` を使用し、`reflection_evaluation` と `retraction_method` および `inverse_retraction_method` によって指定された引き戻しと逆引き戻しに依存します。
  * `reflection_evaluation`: ([`AllocatingEvaluation`](@ref) `R` がインプレースで動作するかアロケーションで動作するか
  * `retraction_method`:     (`default_retraction_metiod(M, typeof(p))`) 使用する引き戻し

      * 反射（`R` を直接設定した場合は無視されます）
      * 緩和ステップ
  * `stopping_criterion`:    ([`StopAfterIteration`](@ref)`(200) |`[`StopWhenChangeLess`](@ref)`(1e-5)`) [`StoppingCriterion`](@ref)。
  * `parallel`:              (`false`) 平行ダグラス・ラチフォードを使用するかどうかを示します。

およびデコレーター用の [`decorate_state!`](@ref) に渡されるもの。

# 出力

得られた（近似的な）最小化子 $p^*$、詳細は [`get_solver_return`](@ref) を参照してください。
