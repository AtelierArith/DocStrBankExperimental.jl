```
genauxga(model::GAModel) :: GAModel auxiliary structure
```

Given model GAM <: GAModel, generate auxiliary scratch space for calculating fitness scores     model = GAM(G1,G2)     aux = genauxga(model) The purpose is to not allocate memory every time you calculate fitness for a new creature.    
