```julia
calc_nis_test(nis_values; num_measurements)

```

Normalized innovation squared (NIS) Test

Double-tailed siginicance test with false alarm probability α = 0.05

Calculates confidence interval [r1 r2] and tests Prob{ ∑ NIS values)} ∈ [r1 r2] ∣ H*0 ) = 1 - α with Hypothesis H*0: N * ∑ NIS values ∼ χ^2_{dof}      dof (degree of freedom): N * m (N: window length, m: dimension of state vector) see https://cs.adelaide.edu.au/~ianr/Teaching/Estimation/LectureNotes2.pdf
