s,f = rdciti(fname)

Read the scattering matrix and frequency list from a CITI file. `s` is a `Complex{Float64}` array of dimension `(n,n,nf)` where `n` is the number of electrical ports of the scattering matrix, and `nf` is the number of frequencies.  `f` is a `Float{64}` vector (or range object) of length `nf` containing the frequencies in GHz.
