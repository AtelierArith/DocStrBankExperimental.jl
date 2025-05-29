linear*system*check: return ||Ax-b||_p

`linear_system_check(:: Union{LinearSystem, LLSModel}, :: AbstractState; pnorm :: Real = Inf, kwargs...)`

注意:

  * state.resのpノルムを返します
  * 何もない場合、state.resが埋められます。
