Main constructor for LQ type

Specifies default argumets for all fields not part of the payoff function or transition equation.

##### Arguments

  * `Q::ScalarOrArray` : `k x k` payoff coefficient for control variable u. Must be symmetric and nonnegative definite
  * `R::ScalarOrArray` : `n x n` payoff coefficient matrix for state variable x. Must be symmetric and nonnegative definite
  * `A::ScalarOrArray` : `n x n` coefficient on state in state transition
  * `B::ScalarOrArray` : `n x k` coefficient on control in state transition
  * `;C::ScalarOrArray{zero(size(R}(1)))` : `n x j` coefficient on random shock in state transition
  * `;N::ScalarOrArray{zero(size(B,1)}(size(A, 2)))` : `k x n` cross product in payoff equation
  * `;bet::Real(1.0)` : Discount factor in `[0, 1]`
  * `capT::Union{Int, Void}(Void)` : Terminal period in finite horizon problem
  * `rf::ScalarOrArray{fill(NaN}(size(R)...))` : `n x n` terminal payoff in finite horizon problem. Must be symmetric and nonnegative definite.
