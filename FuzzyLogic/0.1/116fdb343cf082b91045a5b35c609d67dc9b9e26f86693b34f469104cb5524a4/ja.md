```julia
struct MamdaniFuzzySystem{And<:FuzzyLogic.AbstractAnd, Or<:FuzzyLogic.AbstractOr, Impl<:FuzzyLogic.AbstractImplication, Aggr<:FuzzyLogic.AbstractAggregator, Defuzz<:FuzzyLogic.AbstractDefuzzifier, R<:FuzzyLogic.AbstractRule} <: FuzzyLogic.AbstractFuzzySystem
```

データ構造は、タイプ1のマンダニファジィ推論システムを表します。これは、[`@mamfis`](@ref)マクロを使用して作成できます。与えられた入力でシステムを評価するために関数として呼び出すことができます。入力はキーワード引数として与える必要があります。

  * `name::Symbol`: システムの名前。
  * `inputs::Dictionaries.Dictionary{Symbol, FuzzyLogic.Variable}`: 入力変数と対応するドメイン。
  * `outputs::Dictionaries.Dictionary{Symbol, FuzzyLogic.Variable}`: 出力変数と対応するドメイン。
  * `rules::Vector{R} where R<:FuzzyLogic.AbstractRule`: 推論ルール。
  * `and::FuzzyLogic.AbstractAnd`: ルール内の結合を計算するために使用されるメソッド、デフォルトは[`MinAnd`](@ref)。
  * `or::FuzzyLogic.AbstractOr`: ルール内の選言を計算するために使用されるメソッド、デフォルトは[`MaxOr`](@ref)。
  * `implication::FuzzyLogic.AbstractImplication`: ルール内の含意を計算するために使用されるメソッド、デフォルトは[`MinImplication`](@ref)
  * `aggregator::FuzzyLogic.AbstractAggregator`: ファジィ出力を集約するために使用されるメソッド、デフォルトは[`MaxAggregator`](@ref)。
  * `defuzzifier::FuzzyLogic.AbstractDefuzzifier`: 結果をデフuzzifyするために使用されるメソッド、デフォルトは[`CentroidDefuzzifier`](@ref)。

# 拡張ヘルプ

### 例

```jldoctest; filter=r"Dictionaries\."
fis = @mamfis function tipper(service, food)::tip
    service := begin
      domain = 0:10
      poor = GaussianMF(0.0, 1.5)
      good = GaussianMF(5.0, 1.5)
      excellent = GaussianMF(10.0, 1.5)
    end

    food := begin
      domain = 0:10
      rancid = TrapezoidalMF(-2, 0, 1, 3)
      delicious = TrapezoidalMF(7, 9, 10, 12)
    end

    tip := begin
      domain = 0:30
      cheap = TriangularMF(0, 5, 10)
      average = TriangularMF(10, 15, 20)
      generous = TriangularMF(20, 25, 30)
    end

    service == poor || food == rancid --> tip == cheap
    service == good --> tip == average
    service == excellent || food == delicious --> tip == generous
end

fis(service=1, food=2)

# 出力

1-element Dictionaries.Dictionary{Symbol, Float64}
 :tip │ 5.558585929783786
```
