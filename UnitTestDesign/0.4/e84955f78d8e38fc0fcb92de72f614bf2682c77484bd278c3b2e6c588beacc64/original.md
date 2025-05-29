Greedy Non-deterministic (GND).

This algorithm searches for test cases. It will generate tuples of any order. It generates a different set every time it is invoked.

# Arguments

  * `rng::Random.AbstractRNG`: This option is a random number generator. Set this if you want to generate the same test cases twice in a row.
  * `M::Int`: The number of times it should create a candidate test case each time it creates a candidate. The default is 50. Raising this number could improve test cases and slow generation.

# Extended

This algorithm starts with the seeded test cases and then adds test cases, one at a time. It chooses those parameters that are least used, so far, and then chooses values of those parameters that are least covered by previous tuples. At each step, there is some probability of choosing among nearly-equal next values.

It's not complicated, but it can be slow because every next choice checks against all possible tuples. For large numbers of parameters or large numbers of possible values of each parameter, this generator can be slow, so test it for fewer values first and gradually increase the number of parameters or parameter values.
