```
hasbranching(f, x...)
```

Checks whether the function `f` has branches (if statements) that are dependent on the value x  that would be taken in a tracing system, such as during AD tracing by a package like ReverseDiff.jl.

## Arguments:

```
* `f`: the function to inspect
* `x`: test arguments for the inspection. These values do not need to be the values that
  would be used in the actual calls to the function but instead prototype values which
  match the types that would be used in the actual function call. This is used to trace to
  the correct internal dispatches.
```

## Outputs:

```
Boolean for whether the function has branches.
```

## Customizing and Removing Dispatches from the Checks

Some internal functions of a package may cause false positives because a branch may be known to resolve at compile time. If this is known, then you can add a dispatch to opt that function out of the analysis via:

```julia
function FunctionProperties.Cassette.overdub(::FunctionProperties.HasBranchingCtx, ::typeof(f), x...) 
    f(x...)
end
```
