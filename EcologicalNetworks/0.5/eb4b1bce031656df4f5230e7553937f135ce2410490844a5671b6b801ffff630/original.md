```
omnivory(N::T) where {T <: UnipartiteNetwork}
```

Returns a vector of length richness(N) with an index of consumption across trophic levels. Note we explicitly assume that diet contribution is spread evenly across prey species, in proportion to their degree. Omnivory is measured based on the output of `trophic_level`.

#### References

  * Christensen, Villy, and Daniel Pauly. "ECOPATH II—a software for balancing steady-state ecosystem models and calculating network characteristics." Ecological modelling 61, no. 3-4 (1992): 169-185.
