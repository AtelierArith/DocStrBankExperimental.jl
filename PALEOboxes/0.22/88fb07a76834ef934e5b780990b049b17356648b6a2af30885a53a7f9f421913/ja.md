```
RateStoich(
    ratevartemplate, stoich_statevarname;
    deltavarname_eta=nothing, prcessname="", sms_prefix="", sms_suffix="_sms"
) -> RateStoich
```

反応速度、化学量論、およびオプションで同位体ηを考慮して、生物地球化学反応のフラックスを計算します。

[`create_ratestoich_method`](@ref) と [`add_method_do!`](@ref) を使用して反応に追加します。

反応速度を提供するためにプロパティ変数を設定する必要があります（これは通常、同じ反応の別のメソッドによって実装されます）。このメソッドは、`ratevartemplate`によって供給されたローカル名とリンク名を使用してそれにリンクし、モデル構成に存在しない生成物（`VariableReaction`がリンクされていない）を省略して適切な生成物の速度を計算します。モデル出力を分析する際に使用するメタデータは、通常の場合、`ratevartemplate`として供給されるこの変数に対して [`add_rate_stoichiometry!`](@ref) を使用して追加されます。

# 引数:

  * `ratevartemplate::Union{VarPropT, VarDepT}`: 反応速度変数のローカル名とリンク名を定義するために使用されます。
  * `stoich_statevarname`: タプルのコレクション（化学量論、名前）例 ((-2.0, "O2"), (-1.0,"H2S::Isotope"), (1.0, "SO4::Isotope"))
  * `deltavarname_eta`: 変数デルタ + η のオプションタプル ("SO4*delta", -30.0) または ("SO4*delta", rj.pars.delta)。パラメータが供給されると、これは `do_react_ratestoich` で読み込まれ、修正を可能にします。
  * `processname::String`: モデル出力内の反応の種類を識別するためのオプションタグ
  * `add_rate_stoichiometry=true`: `true` の場合、`ratevartemplate` にメタデータを追加するために [`add_rate_stoichiometry!`](@ref) を呼び出します。

# 例:

反応 2 O2 + H2S -> H2SO4 を表す `RateStoich` を作成します。

```jldoctest; setup = :(import PALEOboxes)
julia> myratevar = PALEOboxes.VarProp("myrate", "mol yr-1", "a rate");

julia> rs = PALEOboxes.RateStoich(myratevar, ((-2.0, "O2"), (-1.0,"H2S"), (1.0, "SO4")));

julia> rs.stoich_statevarname
((-2.0, "O2"), (-1.0, "H2S"), (1.0, "SO4"))
```
