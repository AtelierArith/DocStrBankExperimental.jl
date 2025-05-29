```julia
Ketcham1999FC(
    C0::T = -19.844     # "Simultaneous fit" from Ketcham et al. 1999 apatite
    C1::T = 0.38951     # "Simultaneous fit" from Ketcham et al. 1999 apatite
    C2::T = -51.253     # "Simultaneous fit" from Ketcham et al. 1999 apatite
    C3::T = -7.6423     # "Simultaneous fit" from Ketcham et al. 1999 apatite
    alpha::T = -0.12327 # Box-Cox transform parameter
    beta::T = -11.988   # Box-Cox transform parameter
    l0::T = 16.38       # [um] Initial track length
    l0_sigma::T = 0.09  # [um] Initial track length unertainty
)
```

Fanning Curvilinear apatite annealing model from Ketcham, 1999 (doi: 10.2138/am-1999-0903)
