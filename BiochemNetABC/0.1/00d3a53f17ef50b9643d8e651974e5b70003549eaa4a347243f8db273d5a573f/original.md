`volatile_simulate(sm::SynchronizedModel; p, verbose)`

Simulates a model synchronized with an automaton but does not store the values of the simulation  in order to improve performance. It returns the last state of the simulation `S::StateLHA` not a trajectory `σ::SynchronizedTrajectory`.
