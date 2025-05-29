```
membershiptest(F::AbstractFiber{T}, w:, options=MembershipTestOptions()) where T
```

Check wether the point `w` is contained in the fiber `F`. The tests uses Newton's method with configuration provided by `options`. Returns a [`MembershipTestResult`](@ref).
