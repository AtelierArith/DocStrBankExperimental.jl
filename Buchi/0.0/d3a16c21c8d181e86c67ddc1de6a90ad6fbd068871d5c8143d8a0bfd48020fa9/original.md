SpotAutomaton(w::SpotOmegaWord) SpotAutomaton(d::APDict,[acc::Union{AcceptBuchi,AcceptCoBuchi}],[n::Integer],vs::Pair...)

Create a new automaton over letters of type `Ta`. The arguments are:

  * `d`, an AP dictionary between type `Ta` and BDDs
  * `acc`, an optional acceptance condition (for now, `AcceptBuchi(n)` and `AcceptCoBuchi(n)` are allowed)
  * 
