Linear approximation of branch flow model.

The implementation builds on the second-order cone relaxation of the branch flow model, but neglects the active and reactive loss terms associated with the squared current magnitude so the power flow equations become linear. Note that flow bounds are still second order cones.

```
@article{Baran1989OptimalSystems,
    title = {{Optimal capacitor placement on radial distribution systems}},
    year = {1989},
    journal = {IEEE Transactions on Power Delivery},
    author = {Baran, Mesut E. and Wu, Felix F.},
    number = {1},
    pages = {725--734},
    volume = {4},
    doi = {10.1109/61.19265},
    issn = {19374208}
}
```

Applicable to problem formulations with `_bf` in the name.
