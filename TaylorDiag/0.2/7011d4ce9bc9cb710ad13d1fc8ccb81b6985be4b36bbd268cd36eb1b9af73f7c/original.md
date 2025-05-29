```
taylordiagram(S::AbstractArray,C::AbstractArray,names::Vector{String};figsize=600,dpi=600,pointcolor=:black,pointfontsize=8,correlationcolor=:black,freRMS=5)
taylordiagram(S::AbstractArray,C::AbstractArray;figsize=600,dpi=600,pointcolor=:black,pointfontsize=8,correlationcolor=:black,freRMS=5)
taylordiagram(Cs::Union{Vector{Vector{Float64}}, Vector{Vector{Float32}}, Vector{Vector{Float16}}, Vector{Vector{Int64}}}, names::Vector{String};figsize=600,dpi=600,pointcolor=:black,pointfontsize=8,correlationcolor=:black,freRMS=5)
taylordiagram(Cs::Union{Vector{Vector{Float64}}, Vector{Vector{Float32}}, Vector{Vector{Float16}}, Vector{Vector{Int64}}};figsize=600,dpi=600,pointcolor=:black,pointfontsize=8,correlationcolor=:black,freRMS=5)
```

Compute and plot the Taylor diagram. 4 different versions of the function are available :

  * taylordiagram(S,C,N) plots the standard deviations `S` and correlation coefficients `C` with associated names `N`
  * taylordiagram(S,C) plots the standard deviations `S` and correlation coefficients `C` with names "Obs" and "Mod1..i"
  * taylordiagram(Cs) plots the Taylor diagram for the collections Cs=[Cr, C1, C2, ...] with names "Obs" and "Mod1..i" and compute standard deviations and correlation coefficients
  * taylordiagram(Cs,N) plots the Taylor diagram for the collections Cs=[Cr, C1, C2, ...] with associated names `N` and compute standard deviations and correlation coefficients

# Options

  * `figsize=600` : size of the figure
  * `dpi=600` : dpi of the figure (Dots Per Inch)
  * `pointcolor=:black` : color of the scattered points
  * `pointfontsize=8` : font size of the names of the points
  * `correlationcolor=:black` : color associated with correlation coefficients (dashed lines, 1/4-circle, etc.)
  * `freRMS=5` : frequency of RMSD lines (grey circles)
  * `normalize=false` :  STD normalization
  * `RMSDcolor=:grey` :  RMSD lines and labels colors
  * `ang=pi/2` : angle of the plot (e.g. ang=π/2 then we have 1/4-disc)
  * `std_circ=true` : display or not standard deviation ticks circles (centered on 0)
  * `rmsd_circ=true` : display or not RMSD circles (centered on the data standard deviation)
