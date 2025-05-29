```julia
ScheduledMixing(VIn::N, VOut::N, F::T ; F_args::Tuple = (), F_kwargs::Dict = Dict() , alpha::Float64 = 0.5, iter::Int64 = 1, max_iter::Int64 = 1, Scheduler :: R = QuadraticScheduling, _extra...) --> Dict   where {T<:Function, N<:Union{Number, Vector{<:Number}}, R<:Function}
```

次の内容を含む辞書を返します

  * "VInNext" : VInとVOutの単純な混合で、重みはそれぞれ(1-beta)とbetaであり、ここでbeta = `Scheduler(alpha)`で、イテレーションに応じて変化する可能性があります。
  * "VOutNext" : VInNExtで評価された関数`F`、固定引数`F_args`とキーワード引数`F_kwargs`を使用します。
  * "Delta" : 次の入力と出力の間のノルム差。
  * "kwargs" : この関数自体のキーワード引数で、次の固定点イテレーションでの後続の関数呼び出しに使用されます。ここでは、alphaの値はSchedulerを使用して毎回のイテレーションで更新されます。
