```
preaveraging_end_returns(returns::Array{R,2}, m::Integer) where R<:Real
```

This averages the first few and last few returns. We do this to returns rather than prices (as suggested in BNHLS 2011).

## References

Barndorff-Nielsen, O., Hansen, P.R., Lunde, A., Shephard, N. 2011. - Section 2.2.
