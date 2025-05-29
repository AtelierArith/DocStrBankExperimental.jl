```
sample()：PDMPSampler からサンプルをするための関数．
sample_skeleton() と sample_from_skeleton() の wrapper．

Args:
    N_sk (Int): Number of skeleton points to generate.
    N_samples (Int): Number of final samples to generate from the skeleton.
    xinit (Array{Float64, 1}): Initial position.
    vinit (Array{Float64, 1}): Initial velocity.
    seed (Int): Seed for random number generation.
    verbose (Bool, optional): Whether to print progress information. Defaults to true.

Returns:
    Array{Float64, 2}: Array of samples generated from the PDMP model.
```
