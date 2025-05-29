```
AnnotatedProfile(omics, obs, obsindex)
AnnotatedProfile(op, omicsname, obs, obsindex)
```

# Arguments

  * `omics::Dict{Symbol,OmicsProfile}`: A collection of omics profile with their names in keys.
  * `op::OmicsProfile`: Single omics profile.
  * `omicsname::Symbol`: The name of given `OmicsProfile`.
  * `obs::DataFrame`: The dataframe contains meta information for observations.
  * `obsindex::Symbol`: The index of dataframe `obs`.
