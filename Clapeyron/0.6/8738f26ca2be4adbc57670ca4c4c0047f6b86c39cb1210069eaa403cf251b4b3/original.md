```
ESElectrolyte(solvents::Array{String,1}, 
    ions::Array{String,1}; 
    idealmodel::IdealModel = BasicIdeal,
    neutralmodel::EoSModel = pharmaPCSAFT,
    ionmodel::IonModel = DH,
    RSPmodel::RSPModel = ConstRSP,
    userlocations::Vector{String}=[],
    ideal_userlocations::Vector{String}=[],
    verbose::Bool=false)
```

## Description

This function provides the necessary framework to create an electrolyte model by combining ideal, neutral and ion models:

```julia
model = ESElectrolyte(["water"],["sodium","chloride"];
            idealmodel = BasicIdeal,
            neutralmodel = pharmaPCSAFT,
            ionmodel = DH,
            RSPmodel = ConstRSP)  
```

Any of the available models in Clapeyron can be combined in the above. Note that neutral (solvent) species and ions are defined separately. Within Clapeyron, we will only support ion-based electrolyte models; as such, any salt-based approach (i.e. where the salt is treated as a separate species) will not be supported. 
