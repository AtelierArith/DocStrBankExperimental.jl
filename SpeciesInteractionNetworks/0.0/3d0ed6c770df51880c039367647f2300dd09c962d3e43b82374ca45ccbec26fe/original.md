```
tsvd(N::SpeciesInteractionNetwork, r::Integer)
```

Returns the left and right subspaces for a given ecological network, applying a truncation of the SVD at rank `r`. Note that if `r` is higher than the rank of the network, it will be scaled appropriately.

###### References

[DallaRiva2016Exploring](@citet*)
