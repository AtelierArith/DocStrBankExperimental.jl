```
simulate(state, program, tape_left, tape_right)
```

Simulates one step of the Turing machine: reading, writing, and moving the head.

Inputs

  * `state`::String : curent state of the Turing machine
  * `program`::Dict{Any,Any} with `m` entries: dictionary with keys of [states,read*cells] and values of [next*state,write_cell,movement]
  * `tape_left`::Deque{Int} : values for the stack to the left of the head
  * `tape_right`::Deque{Int} : values for the stack to the right of the head

Outputs

  * `state`::String : updated state of the Turing machine after one simulation step
  * `tape_left`::Deque{Int} : updated values for the stack to the left of the head after one simulation step
  * `tape_right`::Deque{Int} : updated values for the stack to the right of the head after one simulation step
