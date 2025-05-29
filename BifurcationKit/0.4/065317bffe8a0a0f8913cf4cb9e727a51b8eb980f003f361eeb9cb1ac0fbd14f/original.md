```julia
SaveAtEvent(positions; use_newton)

```

This event implements the detection of when the parameter values, used during continuation, equals one of the values in `positions`. This state is then saved in the branch.

For example, you can use it like `continuation(args...; event = SaveAtEvent((1., 2., -3.)))`

The options `use_newton` triggers the use of Newton algorithm to finalise detection.
