```
JuMP.build_variable(_error::Function, ivref::GeneralVariableRef,
                    eval_supports::Dict{Int, Float64}; [check::Bool = true]
                    )::SemiInfiniteVariable{GeneralVariableRef}
```

Extend the `JuMP.build_variable` function to build a semi-infinite variable based on the infinite variable/derivative/parameter function `ivref` with  reduction support `eval_supports`. Will check that input is appropriate if  `check = true`. Errors if `ivref` is not an infinite variable, `eval_supports`  violate infinite parameter domains, or if the support dimensions don't match the  infinite parameter dimensions of `ivref`. This is intended an internal method for  use in evaluating measures.
