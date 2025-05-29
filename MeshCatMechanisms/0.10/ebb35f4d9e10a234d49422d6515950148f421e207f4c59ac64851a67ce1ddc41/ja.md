```
animate(mvis::MechanismVisualizer,
        times::Vector{Float64},
        configurations::Vector{Vector{Float64}};
        fps::Float64=60, realtimerate::Float64=1.)
```

与えられたメカニズムを、構成ベクトルを線形補間することによって、時間でコーディングされた一連の構成を通過させてアニメーションします。
