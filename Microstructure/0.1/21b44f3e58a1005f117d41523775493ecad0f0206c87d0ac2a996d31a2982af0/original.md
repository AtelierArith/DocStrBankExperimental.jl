```
dMRI(nifti::MRI, 
tdelta::Vector{Float64}, 
dsmalldel::Vector{Float64}, 
techo::Vector{Float64}, 
smt::Bool,
nmeas::Vector{Int})
```

Return a dMRI Type object with MRI object `nifti`, and additional volume-wise  experimental settings `tdelta`, `tsmalldel`, `techo`, `smt` for identifing smt signals, and `nmeas` for the number of measurements. 
