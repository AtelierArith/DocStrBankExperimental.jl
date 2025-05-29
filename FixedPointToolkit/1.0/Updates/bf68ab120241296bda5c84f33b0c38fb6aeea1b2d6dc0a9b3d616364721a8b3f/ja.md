```julia
BroydenMixing(VIn::N, VOut::N, F::T ; F_args::Tuple = (), F_kwargs::Dict = Dict() , alpha::Float64 = 0.5, B::Z = alpha*Matrix(1.0I, length(VIn), length(VIn)), _extra...) --> Dict where {T<:Function, N<:Union{Number, Vector{<:Number}}, Z<:Union{Number,Matrix{<:Number}}}
```

辞書を返します。内容は以下の通りです。

  * "VInNext" : VInとVOutの単純な混合で、重みはそれぞれ(1-beta)とbetaで、ここでbeta = `Scheduler(alpha)`であり、イテレーションに応じて変化する可能性があります。
  * "VOutNext" : VInNExtで評価された関数`F`、固定引数`F_args`とキーワード引数`F_kwargs`を使用します。
  * "Delta" : 次の入力と出力の間のノルム差。
  * "kwargs" : この関数自体のキーワード引数で、次の固定点イテレーションでの後続の関数呼び出しに使用されます。ここでは、B行列はBroyden混合ルールに従って毎回更新されます。
