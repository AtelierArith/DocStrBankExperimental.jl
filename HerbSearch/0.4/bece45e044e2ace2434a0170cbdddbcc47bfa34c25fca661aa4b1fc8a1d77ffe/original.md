```
@enum SynthResult optimal_program=1 suboptimal_program=2
```

Representation of the possible results of the synth procedure.  At the moment there are two possible outcomes:

  * `optimal_program`: The synthesized program satisfies the entire program specification.
  * `suboptimal_program`: The synthesized program does not satisfy the entire program specification, but got the best score from the evaluator.
