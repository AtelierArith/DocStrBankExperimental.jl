```
Motility(motile_states::NTuple{N,MotileState}, rates...)
```

Construct a `Motility` from a sequence of `MotileState`s and their transition `rates`.

`motile_states` must be a tuple of `MotileState` instances. `rates` must be specified in the form `(i => j, p)` where `i` is the index of the starting state (as ordered in the `motile_states` tuple), `j` is the index of the state towards which the transition occurs, and `p` is the probability that, after the duration of `i` is over, the transition occurs towards the state `j`. It is not necessary to indicate impossible transitions; any pair `i => j` which is not explicitly specified is assumed to have a transition probability `p=0`.

For example, if we want to define a 3-state motility, composed by a slow but long run, an instantaneous tumble with some `angle_pdf`, and a fast but short run, where the two runs can only transition towards the tumble, but the tumble can transition with probability 30% towards the slow run and 70% towards the fast run, we will call:

```
Motility((Run(10.0, 2.0), Tumble(0.0, angle_pdf), Run(60.0, 0.5)),
    (1 => 2, 1.0),
    (2 => 1, 0.3), (2 => 3, 0.7),
    (3 => 2, 1.0)
)
```

Some default constructors for common motility patterns are provided: `RunTumble`, `RunReverse`, `RunReverseFlick`, `RunStop`
