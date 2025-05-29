`SelfCons{T<:Function, R<:Function, S<:Union{Number, Vector{<:Number}}}` は、固定点を計算したい一般的な関数を表すデータ型です。

# 属性

  * `F               ::  T`: 固定点を計算する必要がある関数。
  * `F_args          ::  Tuple`: 関数 `F` に対して固定された引数のタプル。
  * `F_kwargs        ::  Dict{Symbol, Any}`: 関数 `F` に対して固定されたキーワード引数の辞書。
  * `Initial         ::  S` : 固定点反復を開始するための初期推測。
  * `VIns            ::  Vector{S}`: 固定点反復中に使用されたすべての入力の履歴。
  * `VOuts           ::  Vector{S}`: 固定点反復中に使用されたすべての出力の履歴。
  * `Update          ::  R`: 固定点反復中に使用される更新方法。例: [`SimpleMixing`](@ref)。
  * `Update_kwargs   ::  Dict{Symbol, Any}`: `Update` 関数に対して固定された一部のキーワード引数。

この構造体を初期化するには、次のようにします。

```julia
SelfCons(F::T, Update::R, Initial::S ; F_args::Tuple = (), F_kwargs::Dict = Dict(), Update_kwargs::Dict = Dict()) where {T<:Function, R<:Function, S<:Union{Number, Vector{<:Number}}}
```
