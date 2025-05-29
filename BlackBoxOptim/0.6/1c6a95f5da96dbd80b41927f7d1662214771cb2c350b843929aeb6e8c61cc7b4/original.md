`EpsBoxDominanceFitnessScheme` defines ϵ-box dominance for `N`-tuple (`N`≧1) fitnesses. It operates with fitnesses of type `IndexedTupleFitness`.

`aggregator::AGG` is a function mapping tuple fitness to a single numerical value. Might be used for comparisons (or not, depending on the setup). Always used when printing fitness vectors though.
