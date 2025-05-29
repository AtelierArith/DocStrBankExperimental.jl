`FitnessScheme` defines how fitness vectors/values are compared, presented and aggregated. `Fitness` represents the score of one and the same individual on one or a set of evaluations. A scheme is a specific way to consider the scores in a coherent way. Type parameter `F` specifies the type of fitness values.

`FitnessScheme` could also be used as a function that defines the fitness ordering, i.e. `fs(x, y) == true` iff fitness `x` is better than `y`.
