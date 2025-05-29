`relative_spindle_power(x::Vector{<:AbstractFloat}, fs::Integer)`

The Relative Spindle Power (RSP) algorithm [(Devuyst et al., 2011)](https://pubmed.ncbi.nlm.nih.gov/22254656/)  also detects abnormal values along the spindle frequency band.  For every 1 second window, the amplitude spectrum $S(t)$ is computed,  and the RSP is defined as

$$
RSP(t) = \frac{\int_{11}^{16} S(t, f) df}{\int_{0.5}^{40} S(t, f) df}
$$

This definition is more intelligible than the that of the $\sigma$-index, insofar as it represents the ratio of the total power in the spindle band with respect to the total power in the $[0.5, 40]$ frequency range. It is evident by definition that $0 \leq RSP \leq 1$. Higher values are indicative of a higher spindle probability (it should be clear that $RSP$ is not a probability itself). The rejection threshold recommended in the original paper is $\lambda = 0.22$.
