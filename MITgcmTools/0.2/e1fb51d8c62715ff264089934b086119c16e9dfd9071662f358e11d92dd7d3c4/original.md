MixedLayerDepth(Θ,Σ,Δ,mthd)

Compute mixed layer depth from potential temperature (Θ in °C), salinity (Σ in psu) and depth (Δ in method) according to various formulas (mthd == "BM", "Suga", "Kara"). Inputs must be dense vectors without any missing value (or NaN, etc).

```
D=collect(0.0:1.0:500.0); tmp=(1.0.-tanh.(5*(-1 .+ 2/D[end]*D)));
T=2.0 .+ 8.0*tmp; S=34.0 .+ 0.5*tmp;
(ρP,ρI,ρR) = SeaWaterDensity(T,S,D);

mld=MixedLayerDepth(T,S,D,"BM"); isapprox(mld,134.0)

using Plots
plot(ρP,-D,w=2,label="Potential Density",ylabel="Depth")
plot!(vec([ρP[1] ρP[end]]),-fill(mld,2),label="Mixed Layer Depth",w=2,c="black",s=:dash)
```
