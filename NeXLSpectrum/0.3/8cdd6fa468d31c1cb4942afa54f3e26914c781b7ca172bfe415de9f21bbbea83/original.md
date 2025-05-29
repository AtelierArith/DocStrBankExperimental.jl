```
references(refs::Vector{DirectRefInit}, det::Detector, resp::Matrix{Float64}; minE=0.5e3 )
```

Use along with `direct(...)` to build a collection of direct fitting references.

Example:

```
> detu = matching(unk, 132.0, 110)
> resp = detectorresponse(detu, SDDEfficiency(ModeledWindow(MoxtekAP33())))
> drefs = references([ 
      direct(n"O", stds[1], mat"Al2O3"),
      direct(n"Al", stds[1], mat"Al2O3"),
      direct(n"Ba", stds[2], mat"BaF2"),
      direct(n"Ca", stds[3], mat"CaF2"),
      direct(n"Fe", stds[4], mat"Fe"),
      direct(n"Si", stds[5], mat"Si") ],
      detu, resp
  )
```
