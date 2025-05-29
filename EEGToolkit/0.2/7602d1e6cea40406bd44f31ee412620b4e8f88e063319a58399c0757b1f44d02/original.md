`sigma_index(x::Vector{<:AbstractFloat}, fs::Integer)`

The $\sigma$-index algorithm [(Huupponen et al., 2007)](https://pubmed.ncbi.nlm.nih.gov/17555950/) find abnormally high amplitude values in the spindle frequency band. Per each 1 second window of the EEG, it computes

  * the maximum amplitude in the spindle frequency band, which we call $S_{max}$
  * the average amplitude in the low alpha and theta frequencies, which we call

$\alpha_{mean}, \theta_{mean}$

  * the maximum alpha amplitude $\alpha_{max}$

The $\sigma$-index of each window is defined to be zero if $\alpha_max > S_{max}$, and otherwise

$$
f(S_{max}, \alpha_{mean}, \phi_{mean}) = \frac{2S_{max}}{ \alpha_{mean} + \theta_{mean} } 
$$

Higher values are indicative of a higher spindle probability. The rejection threshold recommended in the original paper is $\lambda = 4.5$.
