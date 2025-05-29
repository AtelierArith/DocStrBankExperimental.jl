```
abstract type AbstractModel{O} end
```

インスタンスオブジェクト（すなわちデータの一部）を与えると、タイプ `O` の結果を出力するシンボリックモデルのための抽象型です。

モデルは、特定の論理言語の式をインスタンスに対してチェックすることに依存する場合に*シンボリック*であると言われます（詳細は[SoleLogics.jl](https://github.com/aclai-lab/SoleLogics.jl)パッケージを参照）。シンボリックモデルは、シンボリックモデルが相互に排他的な論理ルールのセットに合成され、しばしば自然言語に翻訳できるため、透明で*解釈可能なモデリング*の形を提供します。

シンボリックモデルの例には[`Rule`](@ref)s、[`Branch`](@ref)es、[`DecisionList`](@ref)s、[`DecisionTree`](@ref)sがあります。非シンボリック（または*サブシンボリック*）モデルの例には、代数的数学関数をエンコードするもの（例：ニューラルネットワーク）が含まれます。

シンボリックモデルは他の`AbstractModel`をラップし、それらを使用して結果を計算できます。そのため、`AbstractModel`は実際には多くのモデルの合成の結果であり、`AbstractModel`の*ツリー*を含むことができます（葉には`LeafModel`があります）。

# TODO - ここに欠落しているディスパッチを持ってくる（他のモデルタイプについても同様に）

# インターフェース

  * `apply(m::AbstractModel, i::AbstractInterpretation; kwargs...)`
  * `iscomplete(m::AbstractModel)`
  * `outcometype(m::AbstractModel)`
  * `outputtype(m::AbstractModel)`
  * `immediatesubmodels(m::AbstractModel)`
  * `nimmediatesubmodels(m::AbstractModel)`
  * `leafmodels(m::AbstractModel)`
  * `nleafmodels(m::AbstractModel)`
  * `listimmediaterules(m::AbstractModel)`
  * `info(m::AbstractModel, [key, [defaultval]])`
  * `info!(m::AbstractModel, key, value)`
  * `hasinfo(m::AbstractModel, key)`
  * `listrules(m::AbstractModel; kwargs...)`

# ユーティリティ関数

  * `apply(m::AbstractModel, i::AbstractInterpretationSet; kwargs...)`
  * See AbstractTrees...

# ユーティリティ関数

  * `apply(m::AbstractModel, d::AbstractInterpretationSet, i_instance::Integer; kwargs...)
  * `submodels(m::AbstractModel)`(一般的な`AbstractTrees.children(m::AbstractModel)`のフォールバック)
  * `nsubmodels(m::AbstractModel)`
  * `subtreeheight(m::AbstractModel)`
  * `listrules(       m::AbstractModel;       use_shortforms::Bool=true,       use_leftmostlinearform::Union{Nothing,Bool}=nothing,       normalize::Bool=false,       force_syntaxtree::Bool=false,   )`
  * `joinrules(m::AbstractModel, silent=false; kwargs...)`

# 例

TODO

See also [`apply`](@ref), [`Branch`](@ref), [`info`](@ref), [`iscomplete`](@ref), [`LeafModel`](@ref), [`outcometype`](@ref), [`Rule`](@ref).
