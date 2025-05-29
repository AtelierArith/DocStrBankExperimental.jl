```julia
# メソッド (1)
function studentTestIS(y::UniData, ns::IntVec;
                direction::TestDir = Both(),
                equivalent::Bool = true,
                switch2rand::Int = Int(1e8),
                nperm::Int = 20_000, 
                seed::Int = 1234, 
                verbose::Bool = true,
                asPearson::Bool = true) where TestDir <: TestDirection
```
