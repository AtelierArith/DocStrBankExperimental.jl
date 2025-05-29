```
leadfield(hart::Hartmut; type = "cortical")
```

Return the leadfield for the (cortical or artefacual) sources of the HArtMuT model.

# Keyword arguments

  * `type = "cortical"`: Defines whether the "cortical" or "artefactual" leadfield should be returned.

# Returns

  * `Array{Float64, 3}`: Leadfield values i.e. how much each source contributes to the potential measured at each electrode.   The output dimensions are `electrodes x sources x spatial dimension`.

# Examples

```julia-repl
julia> h = Hartmut();
Please cite: HArtMuT: Harmening Nils, Klug Marius, Gramann Klaus and Miklody Daniel - 10.1088/1741-2552/aca8ce

julia> lf = leadfield(h);

julia> size(lf)
(227, 2004, 3)

# Access the leadfield for one spatial dimension
julia> lf[:,:,1]
227×2004 Matrix{Float64}:
  0.151429    0.0284341  …  -0.119927     -0.158114
  0.1732      0.0441432     -0.110515     -0.165316
  0.249592    0.10857       -0.000593027  -0.0206122
  0.245206    0.104854      -0.0200251    -0.055392
  0.126496    0.0118467     -0.128248     -0.146107
  0.253092    0.111688   …   0.02277       0.0184387
  ⋮                      ⋱                
  0.20306     0.138837       0.133486      0.18334
 -0.689154   -1.00904       -0.108276     -0.105398
  0.192729    0.148448       0.0924756     0.142322
 -1.26181    -1.59936       -0.140598     -0.133054
  0.213982    0.145953   …   0.115515      0.170698
  0.0731569   0.0794415      0.0485819     0.107929
```
