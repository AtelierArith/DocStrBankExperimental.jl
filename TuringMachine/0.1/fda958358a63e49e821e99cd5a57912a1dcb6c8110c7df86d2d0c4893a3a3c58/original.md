```
set_up(init_state, input)
```

Performs initial set-up for the simulation of single tape. The `length(input)` must be equal of greater than 1. The input will be placed on tape to the right of the head.

Input

  * `input`::`n`-element Array{Char, 1} : initial data to insert to the right of the head
  * `init_state`::String : string label for initial/starting state of the Turing machine

Outputs

  * `tape_left`::Deque{Int} : initial values for the stack to the left of the head
  * `tape_right`::Deque{Int} : initial values for the stack to the right of the head
