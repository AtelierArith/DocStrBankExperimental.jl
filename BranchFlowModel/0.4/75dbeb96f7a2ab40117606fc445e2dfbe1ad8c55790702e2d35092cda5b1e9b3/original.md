```
check_rank_one(m::JuMP.AbstractModel, net::Network, tol=1e-3)
```

Check the rank of the `m[:H]` matrices from the PSD cone constraints. Warnings express any values with rank greater than one.
