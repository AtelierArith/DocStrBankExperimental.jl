```
DiscretePairCorrelation
```

Represents the pair correlation between two types of particles. The particles could be the same or different species. 

This struct has the field `r`, which represent the radial distance, and the field `g` is the value of the pair correlation. For radial distances `< r[1]` we assume that the pair correlation is zero. For radial distances `> r[end]` we assume the pair correlation is 1. 
