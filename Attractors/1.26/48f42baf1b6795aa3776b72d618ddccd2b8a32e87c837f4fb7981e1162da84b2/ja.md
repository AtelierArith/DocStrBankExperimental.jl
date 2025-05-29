```
StabilityMeasuresAccumulator(mapper::AttractorMapper; kwargs...)
```

初期条件をアトラクタにマッピングしながら、*同時に* 多くの安定性指標を可能な限り効率的に計算する特別なデータ構造です。`mapper` は、`id = mapper(u0)` 構文を実装した任意の [`AttractorMapper`](@ref) のインスタンスです。この機能は [Morr2025](@cite) の一部として開発されました。これを使用する場合は、この論文と Attractors.jl の出版物 [Datseris2023](@cite) を引用してください。

`StabilityMeasuresAccumulator` は、[`basins_fractions`](@ref) のようなライブラリ関数を使用して、任意の `AttractorMapper` として使用できます。すべての初期条件をアトラクタにマッピングした後、[`finalize_accumulator`](@ref) 関数を呼び出す必要があり、これによりアキュムレータによって推定されたすべての安定性指標の辞書が返されます。各辞書は、指標の説明（`String`）をアトラクタ ID を指標値にマッピングする辞書にマッピングします。`reset_mapper!(accumulator)` を呼び出すと、すべての蓄積された指標がクリアされます。

**[`global_continuation`](@ref) との使用**: `StabilityMeasuresAccumulator` は正式には `AttractorMapper` であるため、[`global_continuation`](@ref) と一緒に使用できます。単に `mapper` 入力として [`AttractorSeedContinueMatch`](@ref) に渡し、その後通常通り `global_continuation` を呼び出します。今の唯一の違いは、`global_continuation` が非局所的安定性の指標（バジン分数）を1つだけ返さないことです。むしろ、`global_continuation` の最初の返り値は `measures_cont` となり、非局所的安定性指標（文字列）を辞書のベクトルにマッピングします。各辞書のベクトルは、典型的な [`global_continuation`](@ref) の `fractions_cont` に似ており、各辞書はアトラクタ ID を対応する非局所的安定性指標にマッピングします。

[`stability_measures_along_continuation`](@ref) を使用して、すでに見つかったアトラクタからの `AttractorsViaProximity` マッパーに基づいて計算された安定性指標の継続を行います。これは、収束時間に関連する指標に対して行うのが有用であり、これはより厳密に定義され、近接マッパーに対してより正確に推定されます。

## キーワード引数

  * `finite_time = 1.0`: `finite_time_basin_stability` の計算に考慮される有限時間のホライズン。収束時間が `finite_time` より大きい初期条件は、対応する有限時間バジンに含まれないと見なされます。収束時間は `mapper` によって決定されます。
  * `weighting_distribution::Distribution`: 例えば `basin_stability` の計算に使用される不確実な初期条件の分布。デフォルトでは、状態空間全体で一様分布です。

## 説明

`StabilityMeasuresAccumulator` は、動的システムの各アトラクタに対応する多くの異なる安定性指標の情報を蓄積するために、単一の `id = mapper(u0)` 呼び出しを効率的に使用します。異なる初期条件がそれを通じてマッピングされると、これらの異なる指標がすべて蓄積されます。十分な `u0` がアキュムレータに与えられた後、`finalize!(accumulator)` を使用して最終化（最大値または平均を計算）できます。

以下の安定性指標が各アトラクタに対して推定され（返される辞書は指標の名前を持つ文字列を各アトラクタの指標値を含む辞書にマッピングします）：

### 局所（固定点）安定性指標

これらの指標は固定点アトラクタにのみ適用されます。アトラクタが固定点でない場合（`length(A) > 1`）、その値は `NaN` です。初期条件がそこから始まるなどの理由で不安定な固定点アトラクタが記録された場合、すべての指標に `Inf` の値が割り当てられます。現在、離散時間システムの線形指標は計算されていません。

  * `characteristic_return_time`: 固定点でのヤコビ行列の固有値の最大実部の逆数。
  * `reactivity`: 固定点での線形化されたシステムの最大成長率。詳細は [Krakovska2024ResilienceDynamicalSystems](@cite) を参照してください。
  * `maximal_amplification`: アトラクタでの線形化されたシステムの最大（摂動に関して）増幅。
  * `maximal_amplification_time`: 最大増幅が発生する時間。

### 非局所安定性指標

これらの非局所安定性指標は、初期条件がアトラクタにマッピングされる際に蓄積されます。その後、`finalize_accumulator!` を呼び出す際に、確率密度 `weighting_distribution` に従って平均化されます。ここでの「距離」という言葉は、`metric` キーワードによって確立された距離を指します。

  * `mean_convergence_time`: 収束時間は、[`convergence_time`](@ref) を使用して `mapper` によって決定されます。平均は `weighting_distribution` に関して計算されます。
  * `maximal_convergence_time`: アトラクタへの初期条件の最大収束時間。`weighting_distribution` の下で非ゼロ確率を持つ初期条件のみが考慮されます。
  * `median_convergence_time`: 初期条件の中央値収束時間。`weighting_distribution` の下で非ゼロ確率を持つ初期条件のみが考慮されます。
  * `mean_convergence_pace`: アトラクタへの初期条件の平均収束ペース。平均収束時間と似ていますが、各収束時間はそれぞれの初期条件からアトラクタまでの距離で割られます。
  * `maximal_convergence_pace`: アトラクタへの初期条件の最大収束ペース。`weighting_distribution` の下で非ゼロ確率を持つ初期条件のみが考慮されます。
  * `median_convergence_pace`: 初期条件の中央値収束ペース。`weighting_distribution` の下で非ゼロ確率を持つ初期条件のみが考慮されます。
  * `minimal_critical_shock_magnitude`: 他のアトラクタのバジンの中で、`weighting_distribution` の下で最も近い非ゼロ確率点までのアトラクタの最小距離。単一のアトラクタしか存在しない場合、値 `Inf` が割り当てられます。
  * `maximal_noncritical_shock_magnitude`: 自身のバジンの中で、`weighting_distribution` の下で最も遠い非ゼロ確率点までのアトラクタの距離。単一のアトラクタしか存在しない場合、値 `Inf` が割り当てられます。
  * `mean_noncritical_shock_magnitude`: 上記と同じですが、最大距離ではなく平均距離です。
  * `basin_fraction`: アトラクタに収束する初期条件の割合。
  * `basin_stability`: アトラクタに収束する初期条件の割合で、`weighting_distribution` によって重み付けされています。`weighting_distribution` のデフォルト値の場合、これは `basin_fraction` と同じです。
  * `finite_time_basin_stability`: 時間ホライズン `finite_time` 内でアトラクタに収束する初期条件の割合で、`weighting_distribution` によって重み付けされています。
