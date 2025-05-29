```
FindConfBoundary(DM::AbstractDataModel, Confnum::Real; BoolTest::Bool=(Confnum > 8), Ftest::Bool=false, tol::Real=4e-15)
```

Finds parameter configuration which lies on the boundary of the confidence region of level `Confnum`σ.

  * `BoolTest` can be used to specify whether the threshold is found using a `Bool`-valued test or a `Float`-valued test. Since it uses less memory, the `Bool`-valued test performs better when using `BigFloat` (i.e. when Confnum > 8).
  * `Ftest=true` uses the F-test rather than the Wilks test to define the threshold. Typically, the F-test will yield more conservative estimates (i.e. larger confidence regions) since it accounts for small sample sizes.
