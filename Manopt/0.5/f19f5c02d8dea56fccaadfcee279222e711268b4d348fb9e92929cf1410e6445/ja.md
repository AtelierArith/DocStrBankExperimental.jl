```
LevenbergMarquardt(M, f, jacobian_f, p, num_components=-1; kwargs...)
LevenbergMarquardt(M, vgf, p; kwargs...)
LevenbergMarquardt(M, nlso, p; kwargs...)
LevenbergMarquardt!(M, f, jacobian_f, p, num_components=-1; kwargs...)
LevenbergMarquardt!(M, vgf, p, num_components=-1; kwargs...)
LevenbergMarquardt!(M, nlso, p, num_components=-1; kwargs...)
```

リーマン・レヴェンバーグ-マルクワルトアルゴリズム [Peeters:1993, AdachiOkunoTakeda:2022](@cite) を計算して

$$
\operatorname*{arg\,min}_{p ∈ \mathcal M} \frac{1}{2} \sum_{i=1}^m \lvert f_i(p) \rvert^2
$$

を解きます。

ここで、$f: \mathcal M → ℝ^m$ は成分関数 $f_i: \mathcal M → ℝ$、$i=1,…,m$ で書かれ、各成分関数は連続的に微分可能です。

2番目の署名ブロックは、`p` の最適化をインプレースで実行します。

# 入力

  * `M::`[`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`)``: リーマン多様体 $\mathcal M$
  * `f`: コスト関数 $f: \mathcal M→ℝ^m$。コスト関数は2つの異なる方法で提供できます。

      * ベクトル $f(p) ∈ ℝ^m$ を返す単一の関数として
      * 各単一の関数がスカラー $f_i(p) ∈ ℝ$ を返す関数のベクトルとして

    型は `function_type=` キーワード引数によって決定されます。
  * `jacobian_f`:   $f$ のヤコビアン。ヤコビアンは3つの異なる方法で提供できます。

      * 勾配ベクトルのベクトル $\bigl(\operatorname{grad} f_i(p)\bigr)_{i=1}^m$ を返す単一の関数として
      * 各単一の関数が勾配ベクトル $\operatorname{grad} f_i(p)$ を返す関数のベクトルとして、$i=1,…,m$
      * (係数)行列 $J ∈ ℝ^{m×d}$ を返す単一の関数として、ここで $d$ は多様体の次元です。

    これらの係数は `p` における接空間の [`AbstractBasis`](@extref `ManifoldsBase.AbstractBasis`) に関して与えられます。型は `jacobian_type=` キーワード引数によって決定されます。
  * `p`: 多様体 $\mathcal M$ 上の点
  * `num_components`: コスト関数によって返されるベクトルの長さ $m$。デフォルトではその値は -1 で、これは `f` をもう1回追加で呼び出すことによって自動的に決定されることを意味します。これは `evaluation` が [`AllocatingEvaluation`](@ref) の場合にのみ可能で、変更する評価の場合はこの値を明示的に指定する必要があります。

コストとそのヤコビアンをすでに [`VectorGradientFunction`](@ref) `vgf` として提供することもできます。あるいは、[`NonlinearLeastSquaresObjective`](@ref) `nlso` を渡すこともできます。

# キーワード引数

  * `evaluation=`[`AllocatingEvaluation`](@ref)`()`: 配列を返す関数、例えば点や接ベクトルが、その結果を割り当てることによって動作するか（[`AllocatingEvaluation`](@ref)）、または入力引数を変更してその中で結果を返すか（[`InplaceEvaluation`](@ref)）を指定します。通常、最初の引数は多様体であるため、変更された引数は2番目になります。
  * `η=0.2`:                   新しい提案点を受け入れるために必要な十分なコスト減少閾値のスケーリング係数。許可される範囲: `0 < η < 1`。
  * `expect_zero_residual=false`: アルゴリズムが最小値での残差（目的）の値が0であることを期待するかどうか。
  * `damping_term_min=0.1`:      ダンピング項の初期（および最小）値
  * `β=5.0`:                     現在の新しい点が拒否されたときにダンピング項が乗算されるパラメータ
  * `function_type=`[`FunctionVectorialType`](@ref): 提供されるコスト関数の型を指定する [`AbstractVectorialType`](@ref)。
  * `initial_jacobian_f`:      コスト関数 `f` の初期ヤコビアン。デフォルトでは、これは `num_components` 倍の多様体次元の同様の型の行列です。
  * `initial_residual_values`: コスト関数 `f` の初期残差ベクトル。デフォルトでは、これは `p` と同様の型の長さ `num_components` のベクトルです。
  * `jacobian_type=`[`FunctionVectorialType`](@ref): 提供されるヤコビアンの型を指定する [`AbstractVectorialType`](@ref)。
  * `linear_subsolver!`:    線形部分問題を解く3つの引数 `sk, JJ, grad_f_c` を持つ関数。ここで `JJ` は（数値的な問題を除いて）対称正定値行列です。デフォルト値は [`default*lm*lin_solve!`](@ref)。
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用する再traction $\operatorname{retr}$、再tractionに関するセクションを参照してください [the section on retractions](@extref ManifoldsBase :doc:`retractions`)

他のすべてのキーワード引数は、状態デコレーター用の [`decorate_state!`](@ref) または目的デコレーター用の [`decorate_objective!`](@ref) に渡されます。

# 出力

得られた近似最小化点 $p^*$。ソルバーの全体的な最終状態を取得するには、特に `return_state=` キーワードについての詳細は [`get_solver_return`](@ref) を参照してください。 ```
