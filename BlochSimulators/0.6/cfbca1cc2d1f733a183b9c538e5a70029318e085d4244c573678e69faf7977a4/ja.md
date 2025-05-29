```
simulate_derivatives_finite_difference(
    requested_derivatives::Tuple{Vararg{Symbol}},
    echos::AbstractMatrix{<:Complex},
    sequence::BlochSimulator,
    parameters::StructVector{<:AbstractTissueProperties},
    stepsizes::T₁T₂B₁B₀=DEFAULT_STEPSIZES
)
```

事前に計算されたエコー（`ctx`に含まれる）に対して、`requested_derivatives`にある（非線形の）組織特性に関する偏微分を有限差分法を用いて計算します。

# 引数

  * `requested_derivatives::Tuple{Vararg{Symbol}}`: 偏微分を計算したい（非線形の）組織特性に対応するシンボルのタプル（例: (:T₁, :T₂, :B₁)）。
  * `echos::AbstractMatrix`: すべてのボクセルに対するすべてのエコー時間での磁化の事前計算された行列。
  * `sequence::BlochSimulator`: 基本的なMRパルスシーケンスを表すシミュレーター。
  * `parameters::SimulationParameters`: `echos`を生成するために使用されるシミュレーションパラメータ（すべてのボクセルにおいて）。
  * `stepsizes::T₁T₂B₁B₀`: 各異なる組織特性に対する有限差分計算のためのステップサイズ。デフォルトのステップサイズは`DEFAULT_STEPSIZES_FINITE_DIFFERENCE`に提供されています。

# 戻り値

  * `∂echos`: `ctx.echos`に対する各`requested_derivatives`に関する偏微分を含むNamedTuple。すなわち、∂echos.T₁はT₁に関する偏微分を含み、∂echos.T₂はT₂に関する偏微分を含みます。

# 注意事項

  * 非線形の組織特性に対する偏微分のみを計算します。線形の組織特性（例: プロトン密度）に対しては、`echos`自体以上のものは必要ありません。
