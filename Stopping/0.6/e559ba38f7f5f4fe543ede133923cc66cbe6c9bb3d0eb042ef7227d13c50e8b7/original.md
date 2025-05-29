Type: list of States

Constructor:

`ListofStates(:: AbstractState)`

`ListofStates(n :: Int, :: Val{AbstractState})`

`ListofStates(n :: Int, list :: Array{AbstractState,1})`

`ListofStates(state :: S; n :: Int = -1, kwargs...)`

Note:

  * If `n != -1`, then it stores at most n `AbstractState`.
  * `ListofStates` recursively handles sub-list of states as the attribute list is

an array of pair whose first component is a, `AbstractState` and the second component is a `ListofStates` (or `VoidListofStates`).

Examples: `ListofStates(state)`     `ListofStates(state, n = 2)`     `ListofStates(-1, Val{NLPAtX}())`     `ListofStates(-1, [(state1, VoidListofStates), (state2, VoidListofStates)], 2)`    
