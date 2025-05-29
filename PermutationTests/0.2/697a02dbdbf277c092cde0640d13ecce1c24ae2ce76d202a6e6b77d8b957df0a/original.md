```julia
# METHOD (1)
function anovaMcTestIS(Y::UniDataVec, ns::IntVec;
                direction::TestDir = Both(),
                switch2rand::Int = max(Int(1e8) ÷ length(𝐘), Int(1e4)),
                nperm::Int = 20_000, 
                seed::Int = 1234, 
                verbose::Bool = true,
                #
                stepdown::Bool = true,
                fwe::Float64 = 0.05,
                threaded::Bool = Threads.nthreads()>=4) where TestDir <: TestDirection
```
