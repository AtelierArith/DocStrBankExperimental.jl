```julia
# 方法 (1)
function anovaTestRM(y::UniData, ns::@NamedTuple{n::Int, k::Int};
            direction::TestDir = Both(),
            equivalent::Bool = true,
            switch2rand::Int = Int(1e8),
            nperm::Int = 20_000, 
            seed::Int = 1234, 
            verbose::Bool = true) where TestDir <: TestDirection
```
