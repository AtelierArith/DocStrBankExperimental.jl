add_to_list!: add a State to the list of maximal size n. If a n+1-th State is added, the first one in the list is removed. The given is State is compressed before being added in the list (via State.copy_compress_state).

`add_to_list!(:: AbstractListofStates, :: AbstractState; kwargs...)`

Note: 

  * kwargs are passed to the compress_state call.
  * does nothing for `VoidListofStates`

see also: ListofStates, State.compress_state, State.copy_compress_state
