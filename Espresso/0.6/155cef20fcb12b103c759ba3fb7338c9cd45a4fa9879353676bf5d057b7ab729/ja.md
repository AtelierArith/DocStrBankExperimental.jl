```
args = [:m, :x, :y]
types = (Linear, Matrix{Float64}, Matrix{Float64})
ex = :(sum((m.W * x .+ m.b) - y))

destruct(args, types, ex)
# ==>
# ([:m_W, :m_b, :x, :y],
#  :(sum((m_W * x .+ m_b) - y)),
#  Dict(:(m.W) => :m_W, :(m.b) => :m_b))
```
