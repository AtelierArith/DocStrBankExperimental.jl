BPINN Solution contains the original solution from AdvancedHMC.jl sampling (BPINNstats contains fields related to that).

1. `ensemblesol` is the Probabilistic Estimate (MonteCarloMeasurements.jl Particles type) of Ensemble solution from All Neural Network's (made using all sampled parameters) output's.
2. `estimated_nn_params` - Probabilistic Estimate of NN params from sampled weights, biases.
3. `estimated_de_params` - Probabilistic Estimate of DE params from sampled unknown DE parameters.
