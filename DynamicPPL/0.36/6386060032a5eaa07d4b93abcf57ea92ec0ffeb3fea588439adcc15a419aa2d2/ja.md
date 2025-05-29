```
LogDensityFunction(
    model::Model,
    varinfo::AbstractVarInfo=VarInfo(model),
    context::AbstractContext=DefaultContext();
    adtype::Union{ADTypes.AbstractADType,Nothing}=nothing
)
```

モデルと、次のために必要なすべての情報を含む構造体：

  * 指定された点での対数密度を計算すること。
  * もし `adtype` が提供されていれば、その点での対数密度の勾配を計算すること。

基本的なレベルでは、LogDensityFunctionはモデルをその使用されるvarinfoの型とともにラップし、評価コンテキストを含みます。これらは対数密度を計算するために知られている必要があります（[`DynamicPPL.evaluate!!`](@ref)を使用）。

`adtype` キーワード引数が提供されている場合、この構造体は対数密度の勾配の効率的な計算のために他の情報とともにadtypeも保存します。ADタイプ `AutoBackend()` で `LogDensityFunction` を準備するには、ADバックエンド自体がロードされている必要があります（例：`import Backend`）。

`DynamicPPL.LogDensityFunction` は LogDensityProblems.jl インターフェースを実装しています。`adtype` が何もない場合、`logdensity` のみが実装されます。`adtype` が具体的なADバックエンドタイプである場合、`logdensity_and_gradient` も実装されます。

# フィールド

  * `model`: 評価に使用されるモデル
  * `varinfo`: 評価に使用されるvarinfo
  * `context`: 評価に使用されるコンテキスト; `nothing` の場合、適用可能なときに `leafcontext(model.context)` が使用されます
  * `adtype`: 対数密度勾配の評価に使用されるADタイプ。`nothing` の場合、勾配は計算できません
  * `prep`: （内部使用のみ）モデルのための勾配準備オブジェクト

# 例

```jldoctest
julia> using Distributions

julia> using DynamicPPL: LogDensityFunction, contextualize

julia> @model function demo(x)
           m ~ Normal()
           x ~ Normal(m, 1)
       end
demo (generic function with 2 methods)

julia> model = demo(1.0);

julia> f = LogDensityFunction(model);

julia> # LogDensityProblems.jlのインターフェースを実装しています。
       using LogDensityProblems

julia> LogDensityProblems.logdensity(f, [0.0])
-2.3378770664093453

julia> LogDensityProblems.dimension(f)
1

julia> # デフォルトでは内部で `VarInfo` を使用しますが、これは必須ではありません。
       f = LogDensityFunction(model, SimpleVarInfo(model));

julia> LogDensityProblems.logdensity(f, [0.0])
-2.3378770664093453

julia> # これは `model` のコンテキストも尊重します。
       f_prior = LogDensityFunction(contextualize(model, DynamicPPL.PriorContext()), VarInfo(model));

julia> LogDensityProblems.logdensity(f_prior, [0.0]) == logpdf(Normal(), 0.0)
true

julia> # 勾配も計算する必要がある場合、ADバックエンドを指定できます。
       import ForwardDiff, ADTypes

julia> f = LogDensityFunction(model, adtype=ADTypes.AutoForwardDiff());

julia> LogDensityProblems.logdensity_and_gradient(f, [0.0])
(-2.3378770664093453, [1.0])
```
