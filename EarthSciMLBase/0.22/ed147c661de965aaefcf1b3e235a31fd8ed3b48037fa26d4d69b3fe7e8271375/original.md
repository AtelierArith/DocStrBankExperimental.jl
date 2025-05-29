Operators are objects that modify the current state of a `Simulator` system. Each operator should be define a function with the signature:

```
`EarthSciMLBase.get_scimlop(::Operator, csys::CoupledSystem, mtk_sys, coord_args,
    domain::DomainInfo, u0, p, alg::MapAlgorithm)::AbstractSciMLOperator`
```

which should return a [SciMLOperators.AbstractSciMLOperator](https://docs.sciml.ai/SciMLOperators/stable/interface/). Refer to the [SciMLOperators.jl](https://docs.sciml.ai/SciMLOperators/stable/) documentation for more information on how to define operators.

Operators should also define a function with the signature:

```
`EarthSciMLBase.get_needed_vars(op::Operator, csys, mtk_sys, domain::DomainInfo)`
```

which should return a list of variables that are needed by the operator.
