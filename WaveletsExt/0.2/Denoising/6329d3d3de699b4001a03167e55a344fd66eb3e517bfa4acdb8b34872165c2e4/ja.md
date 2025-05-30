```
denoiseall(x, inputtype, wt[; L=maxtransformlevels(size(x,1)),
    tree=maketree(size(x,1), L, :dwt), dnt=VisuShrink(size(x,1)),
    estnoise=noisest, bestTH=nothing, smooth=:regular])
```

複数の信号を入力タイプ `inputtype` でデノイズします。

# 引数:

  * `x::AbstractArray{<:Number}`: 入力信号/係数。
  * `inputtype::Symbol`: `x` の入力タイプ。現在受け入れられている入力タイプは

      * `:sig`: 元の信号; `x` は各列が信号を表す2-D配列である必要があります。
      * `:dwt`: `dwt` 変換された信号係数; `x` は各列が信号の係数を表す2-D配列である必要があります。
      * `:wpt`: `wpt` 変換された信号係数; `x` は各列が信号の係数を表す2-D配列である必要があります。
      * `:sdwt`: `sdwt` 変換された信号係数; `x` は各2-Dスライスが信号の係数を表す3-D配列である必要があります。
      * `:swpd`: `swpd` 変換された信号係数; `x` は各2-Dスライスが信号の係数を表す3-D配列である必要があります。
      * `:acdwt`: AutocorrelationShell.jl からの `acdwt` 変換された信号係数; `x` は各2-Dスライスが信号の係数を表す3-D配列である必要があります。
      * `:acwpd`: AutocorrelationShell.jl からの `acwpd` 変換された信号係数; `x` は各2-Dスライスが信号の係数を表す3-D配列である必要があります。
  * `wt::Union{DiscreteWavelet, Nothing}`: 分解に使用される離散ウェーブレット（入力タイプ `:sig` 用）および再構成。再構成が必要ない場合は `nothing` を指定できます。
  * `L::Integer`: 分解レベルの数。入力タイプ `:sig`、`:dwt`、および `:sdwt` に必要です。デフォルト値は `maxtransformlevels(size(x,1))` に設定されています。
  * `tree::BitVector`: 信号の分解ツリー。入力タイプ `:wpt` および `:swpd` に必要です。デフォルト値は `maketree(size(x,1), L, :dwt)` に設定されています。
  * `dnt::DNFT`: デノイズタイプ。デフォルトタイプは `VisuShrink(size(x,1))` に設定されています。
  * `estnoise::Union{Function, Vector{<:Number}}`: ノイズ推定。信号のノイズを推定するための関数として、または推定されたノイズのベクトルとして入力できます。デフォルトは `noisest` 関数に設定されています。
  * `bestTH::Union{Function, Nothing}`: 信号のグループに対して最適な閾値を決定する方法。`nothing` が指定された場合、各信号は `dnt` および `estnoise` パラメータから決定されたそれぞれの最適な閾値でデノイズされます。そうでない場合は、閾値のベクトルから最適な閾値を決定するための関数を渡すことができます。例えば: `mean` や `median`。デフォルトは `nothing` に設定されています。
  * `smooth::Symbol`: 使用される平滑化方法。`:regular` 平滑化は与えられたすべての係数を閾値処理しますが、`:undersmooth` 平滑化はウェーブレット変換の最低周波数サブスペースノードを閾値処理しません。デフォルトは `:regular` に設定されています。

**関連情報:** [`denoise`](@ref), [`noisest`](@ref), [`relerrorthreshold`](@ref)
