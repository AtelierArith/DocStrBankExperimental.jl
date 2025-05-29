```
CovarianceWorkspace(m_i, m_j, m_p, m_q; lmax::Int=0)
```

Inputs and cache for covariance calculations. A covariance matrix relates the masks of four fields and spins. This structure caches various cross-spectra between masks and noise-weighted masks. By default, operates at Float64 precision.

# Arguments:

  * `m_i::CovField{T}`: map i
  * `m_j::CovField{T}`: map j
  * `m_p::CovField{T}`: map p
  * `m_q::CovField{T}`: map q

# Keywords

  * `lmax::Int=0`: maximum multipole to compute covariance matrix
