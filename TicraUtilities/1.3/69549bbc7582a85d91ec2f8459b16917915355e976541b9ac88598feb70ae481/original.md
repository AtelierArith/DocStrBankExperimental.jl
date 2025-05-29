```
SPHQPartition
```

Struct containing all the data read from a Ticra-compatible Q-type SPH file for one frequency. The `qsmns` field contains the Q coefficients. It is indexed as `qsmns[s,m,n]` where `s ∈ {1,2}`, `m ∈ -mmax:mmax`,  `n ∈ {1, ..., mmax}`.  But not all entries are used.  The only possible nonzero entries are where  `n ∈ {max(1, abs(m)), ..., nmax}`.  Note that if the coefficients stored in the SPH files are `Q'`, and the cofficients stored in a `SPHQPartition` instance are `Q`, then `Q = sqrt(8π) * conj(Q')`, as discussed in the File Formats section of the Ticra official documentation.

### Fields

  * `prgtag::String`: Program tag and time stamp, from the program that created the file.
  * `idstrg::String`: Identification text.
  * `nthe::Int`: Number of θ-samples over 360°. Must be even and ≥ 4.
  * `nphi::Int`: Number of ϕ-samples over 360°. Must be ≥ 3.
  * `nmax::Int`: Maximum value for polar index `n` in the SW expansion. `1 ≤ nmax ≤ nthe÷2`.
  * `mmax::Int`: Maximum value for azimuthal index `|m|` in the SW expansion. 0 ≤ mmax ≤ min((nphi-1)÷2, nmax).
  * `t4::String`: Dummy string.
  * `t5::String`: Dummy string.  If parsed, contains 5 real numbers.
  * `t6::String`: Dummy string.  If parsed, contains 5 real numbers.
  * `t7::String`: Dummy string.
  * `t8::String`: Dummy string.
  * `qsmns::OffsetArray{ComplexF64, 3}`: Contains the Q coefficients, assuming exp(jωt) time variation and using the Ticra normalization convention.  The array has axes `(1:2, -mmax:mmax, 1:nmax)`, meaning that some of the entries (those with `n < abs(m)`) are always zero.
  * `powerms::OffsetArray{Float64, 1}`: The vector has axes `(0:mmax)` and the `m`th element contains the total power (one-half the sum of the magnitude squared) of all modes with `±m` as the m index.
