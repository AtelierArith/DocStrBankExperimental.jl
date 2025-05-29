```
integrationdata(
    self::IntegDomain,
    integration_rule::IR,
) where {IR<:AbstractIntegRule}
```

Calculate the data needed for a given numerical quadrature rule.

For given integration domain, compute the quantities needed for numerical integration. The integration rule does not necessarily have to be the one associated originally with the integration domain.

# Return

`npts`, `Ns`, `gradNparams`, `w`, `pc` = number of quadrature points, arrays of basis function values at the quadrature points,  arrays of gradients of basis functions  with respect  to the parametric coordinates, array of weights and array of locations of the quadrature points.
