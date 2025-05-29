```
run!(simulation; pickup=false)
```

Run a `simulation` until one of `simulation.stop_criteria` evaluates `true`. The simulation will then stop.

# Picking simulations up from a checkpoint

Simulations are "picked up" from a checkpoint if `pickup` is either `true`, a `String`, or an `Integer` greater than 0.

Picking up a simulation sets field and tendency data to the specified checkpoint, leaving all other model properties unchanged.

Possible values for `pickup` are:

  * `pickup=true` picks a simulation up from the latest checkpoint associated with the `Checkpointer` in `simulation.output_writers`.
  * `pickup=iteration::Int` picks a simulation up from the checkpointed file associated  with `iteration` and the `Checkpointer` in `simulation.output_writers`.
  * `pickup=filepath::String` picks a simulation up from checkpointer data in `filepath`.

Note that `pickup=true` and `pickup=iteration` fails if `simulation.output_writers` contains more than one checkpointer.
