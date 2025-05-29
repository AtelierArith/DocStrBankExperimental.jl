```
compute_ASRQ(f::Vector{Float64})
```

Compute assimilate requirement, CO2 production factor and carbon content according to Penning de Vries et al. 1982. These values can be used to compute growth respiration. Different tissues (species/organ) have different composition. Growth costs are computed given the fraction of dry matter allocated to different carbon pools according to specific composition of the tissue:     f = [carbohydrates, proteins, lipids, lignin, organic acids, minerals]

```
The assimilate requirement (ASRQ, g) is the amount of assimilates required to produce 1 g of dry matter.
The CO2 production factor (CO2PFF, g) is the amount of CO2 produced per g of dry matter.
The carbon fraction (CF, %) is the fraction of dry matter that is carbon.
```

Citations: Penning de Vries, F. W. T., & van Laar, H. H. (1982). Simulation of growth processes and the model BACROS. In F. W. T. Penning de Vries, & H. H. van Laar (Eds.), Simulation of plant growth and crop production (pp. 114-135). (Simulation monographs). Pudoc. https://edepot.wur.nl/172216
