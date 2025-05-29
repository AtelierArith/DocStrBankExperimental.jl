```
DVec{K,V,D<:AbstractDict{K,V},S}
```

FCIQMCおよび[KrylovKit](https://github.com/Jutho/KrylovKit.jl)で使用するための辞書ベースのベクトルのようなデータ構造です。主に`Dict`のように振る舞いますが、`norm`や`dot`などのさまざまな線形代数演算をサポートしています。FCIQMCアルゴリズムで適切な生成戦略を選択するために使用される[`StochasticStyle`](@ref)があります。

関連項目: [`AbstractDVec`](@ref), [`InitiatorDVec`](@ref), [`PDVec`](@ref)。

## コンストラクタ

  * `DVec(dict::AbstractDict[; style, capacity])`: `dict`をストレージとして持つ`DVec`を作成します。データがコピーされる場合とされない場合がありますので注意してください。
  * `DVec(args...[; style, capacity])`: `args...`は`Dict`コンストラクタに渡されます。ストレージには`Dict`が使用されます。
  * `DVec{K,V}([; style, capacity])`: 空の`DVec{K,V}`を作成します。
  * `DVec(dv::AbstractDVec[; style, capacity])`: `adv`と同じ内容の`DVec`を作成します。デフォルトでは`style`は`dv`から継承されます。

デフォルトの`style`は`DVec`の`valtype`に基づいて選択されます（[`default_style`](@ref)を参照）。スタイルが指定され、`valtype`が`style`の`eltype`と一致しない場合、値は適切な型に変換されます。

容量引数はオプションで、`Base.sizehint!`を介して`DVec`の初期サイズを設定します。

## 例

```jldoctest
julia> dv = DVec(:a => 1)
DVec{Symbol,Int64} with 1 entry, style = IsStochasticInteger{Int64}()
  :a => 1

julia> dv = DVec(:a => 2, :b => 3; style=IsDeterministic())
DVec{Symbol,Float64} with 2 entries, style = IsDeterministic{Float64}()
  :a => 2.0
  :b => 3.0
```
