```
general_mixed_increment!(material::AbstractMaterial,
                         dstrain_knowns::AbstractVector{<:Union{T, Missing}},
                         dstress_knowns::AbstractVector{<:Union{T, Missing}},
                         dt::Real,
                         dstrain::AbstractVector{<:Union{T, Missing}}=dstrain_knowns,
                         max_iter::Integer=50, norm_acc::T=1e-9) where T <: Real
```

Find a compatible strain increment for `material`. A combination of `general_increment!` and `stress_driven_general_increment!`, which allows for loadings where some components are strain-driven and some are stress-driven, such as the biaxial "bow-tie" and "reverse bow-tie" loadings of:

```
Corona, E., Hassan, T. and Kyriakides, S. (1996) On the Performance of
Kinematic Hardening Rules in Predicting a Class of Biaxial Ratcheting
Histories. International Journal of Plasticity, Vol 12, pp. 117--145.
```

See also:

```
Bari, Shafiqul. (2001) Constitutive modeling for cyclic plasticity and ratcheting.
Ph.D. thesis, North Carolina State University.
```

which compares the response of several different plasticity models under these loadings.

Each known component must be either strain-driven or stress-driven, not both.

The combination of the known components of dstrain and dstress must describe a valid material state. Otherwise the optimizer may fail to converge, or return a nonsensical solution.
