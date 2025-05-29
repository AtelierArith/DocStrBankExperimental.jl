```julia
# METHOD (1)
function anovaTestIS(y::UniData, ns::IntVec;
                direction::TestDir = Both(),
                equivalent::Bool = true,
                switch2rand::Int = Int(1e8),
                nperm::Int = 20_000, 
                seed::Int = 1234, 
                verbose::Bool = true) where TestDir <: TestDirection
```
