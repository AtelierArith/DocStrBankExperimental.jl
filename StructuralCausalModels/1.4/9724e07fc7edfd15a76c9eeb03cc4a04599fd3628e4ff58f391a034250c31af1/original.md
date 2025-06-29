# shipley_test

```julia
shipley_test(d)

```

Test of all independencies implied by a given DAG

Computes a simultaneous test of all independence relationships implied by a given Gaussian model defined according to a directed acyclic graph, based on the sample covariance matrix.

The test statistic is C = -2 sum(ln(p*j)) where p*j are the p-values of tests of conditional independence in the basis set computed by basiSet(A). The p-values are independent uniform variables on (0,1) and the statistic has exactly a chi square distribution on 2k degrees of freedom where k is the number of elements of the basis set.  Shipley (2002) calls this test Fisher's C test.

### Method

```julia
shipley_test(;
* `d::Dag`                             : Directed acyclic graph
)
```

### Returns

```julia
* `res::NamedTuple`                    : (ctest=..., dof=..., pval=...)
```

where:

ctest: Test statistic C   dof:   Degrees of freedom.   pval:  The P-value of the test, assuming a two-sided alternative.

# Extended help

### Example

### Shipley_test for the mathematics marks data

```julia
using StructuralCausalModels, RData

objs = RData.load(scm_path("..", "data", "marks.rda");
marks_df = objs["marks"]

d = OrderedDict(
  :mechanics => [:vectors, :algebra],
  :vectors => [:algebra],
  :statistics => [:algebra, :analysis],
  :analysis => [:algebra]
);
dag = Dag(d; df=df)
shipley_test(dag)
```

### See also

```julia
?Dag
?basis_set
?pcor_test
```

### Acknowledgements

Original author:                       Giovanni M. Marchetti

Translated to Julia:                   Rob J Goedman

### References

Shipley, B. (2000). A new inferential test for path models based on directed acyclic graphs. Structural Equation Modeling, 7(2), 206–218.

### Licence

The R package ggm is licensed under License: GPL-2.

The Julia translation is licenced under: MIT.

Part of the api, exported.
