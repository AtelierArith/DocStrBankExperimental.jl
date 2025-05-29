```
InitiatorDVec{K,V} <: AbstractDVec{K,V}
```

[`ProjectorMonteCarloProblem`](@ref Main.ProjectorMonteCarloProblem) および [`KrylovKit.jl`](https://github.com/Jutho/KrylovKit.jl) で使用するための辞書ベースのベクトルライクデータ構造です。 [`AbstractDVec`](@ref) を参照してください。 [`DVec`](@ref) と機能的に同一ですが、イニシエータメソッドを促進するために内部に [`InitiatorValue`](@ref) を含んでいます。モンテカルロ符号問題を制御するためのイニシエータメソッドは、[J. Chem. Phys. 132, 041103 (2010)](https://doi.org/10.1063/1.3302277) で初めて導入されました。イニシエータの取り扱いは、`initiator` キーワード引数で [`InitiatorRule`](@ref) を指定することによって制御されます（以下を参照）。

他にも: [`AbstractDVec`](@ref), [`DVec`](@ref), [`PDVec`](@ref)。

## コンストラクタ

  * `InitiatorDVec(dict::AbstractDict[; style, initiator, capacity])`: ストレージ用に `dict` を持つ `InitiatorDVec` を作成します。データがコピーされる場合とされない場合がありますので注意してください。
  * `InitiatorDVec(args...[; style, initiator, capacity])`: `args...` は `Dict` コンストラクタに渡されます。ストレージ用に `Dict` が使用されます。
  * `InitiatorDVec{K,V}([; style, initiator, capacity])`: 空の `InitiatorDVec{K,V}` を作成します。
  * `InitiatorDVec(dv::AbstractDVec[; style, initiator, capacity])`: `dv` と同じ内容を持つ `InitiatorDVec` を作成します。デフォルトでは、`style` は `dv` から継承されます。

## キーワード引数

  * `style`: 有効な [`StochasticStyle`](@ref)。デフォルトは `InitiatorDVec` の `valtype` に基づいて選択されます（[`default_style`](@ref) を参照）。スタイルが指定され、`valtype` がスタイルの `eltype` と一致しない場合、値は適切な型に変換されます。
  * `initiator = Initiator(1)`: 有効な [`InitiatorRule`](@ref)。[`Initiator`](@ref) を参照してください。
  * `capacity`: `Int` としての指標サイズ。オプションです。`Base.sizehint!` を介して `InitiatorDVec` の初期サイズを設定します。
