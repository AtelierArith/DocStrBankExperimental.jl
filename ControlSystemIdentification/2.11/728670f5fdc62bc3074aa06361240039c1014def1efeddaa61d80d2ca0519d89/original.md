```
res = n4sid(data, r=:auto; verbose=false)
```

Estimate a statespace model using the n4sid method. Returns an object of type [`N4SIDStateSpace`](@ref) where the model is accessed as `res.sys`.

Implements the simplified algorithm (alg 2) from "N4SID: Subspace Algorithms for the Identification of Combined Deterministic Stochastic Systems" PETER VAN OVERSCHEE and BART DE MOOR

The frequency weighting is borrowing ideas from "Frequency Weighted Subspace Based System Identification in the Frequency Domain", Tomas McKelvey 1996. In particular, we apply the output frequency weight matrix (Fy) as it appears in eqs. (16)-(18).

# Arguments:

  * `data`: Identification data `data = iddata(y,u)`
  * `r`: Rank of the model (model order)
  * `verbose`: Print stuff?
  * `Wf`: A frequency-domain model of measurement disturbances. To focus the attention of the model on a narrow frequency band, try something like `Wf = Bandstop(lower, upper, fs=1/Ts)` to indicate that there are disturbances *outside* this band.
  * `i`: Algorithm parameter, generally no need to tune this
  * `γ`: Set this to a value between (0,1) to stabilize unstable models such that the largest eigenvalue has magnitude γ.
  * `zeroD`: defaults to false

See also the newer implementation [`subspaceid`](@ref) which allows you to choose between different weightings (n4sid being one of them). A more accurate prediciton model can sometimes be obtained using [`newpem`](@ref), which is also unbiased for closed-loop data.
