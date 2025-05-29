```julia
struct SugenoFuzzySystem{And<:FuzzyLogic.AbstractAnd, Or<:FuzzyLogic.AbstractOr, R<:FuzzyLogic.AbstractRule} <: FuzzyLogic.AbstractFuzzySystem
```

データ構造は、タイプ1のSugenoファジィ推論システムを表します。これは[`@sugfis`](@ref)マクロを使用して作成できます。与えられた入力でシステムを評価するために関数として呼び出すことができます。入力はキーワード引数として与える必要があります。

  * `name::Symbol`: システムの名前。
  * `inputs::Dictionaries.Dictionary{Symbol, FuzzyLogic.Variable}`: 入力変数と対応するドメイン。
  * `outputs::Dictionaries.Dictionary{Symbol, FuzzyLogic.Variable}`: 出力変数と対応するドメイン。
  * `rules::Vector{R} where R<:FuzzyLogic.AbstractRule`: 推論ルール。
  * `and::FuzzyLogic.AbstractAnd`: ルール内の結合を計算するために使用されるメソッド、デフォルトは[`MinAnd`](@ref)。
  * `or::FuzzyLogic.AbstractOr`: ルール内の選言を計算するために使用されるメソッド、デフォルトは[`MaxOr`](@ref)。
