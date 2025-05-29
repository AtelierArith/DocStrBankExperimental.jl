results(FastNet)        

Return a refernce to the results of *sim* as a DataFrame

# Example

```jldoctest
julia> using Fastnet

julia> net=FastNet(1000,2000,2,[]);

julia> makenodes!(net,12,1)

julia> makenodes!(net,34,2)

julia> sim=FastSim(net,(r,t)->nothing,[])
Simulation run, currently at time 0.0

julia> runsim!(sim,100,25)
Time     Node state 1    Node state 2
  0.0              12              34
 25.0              12              34
 50.0              12              34
 75.0              12              34
100.0              12              34

julia> results(sim)
5×3 DataFrame
 Row │ Time     Node state 1  Node state 2 
     │ Float64  Int64         Int64        
─────┼─────────────────────────────────────
   1 │     0.0            12            34
   2 │    25.0            12            34
   3 │    50.0            12            34
   4 │    75.0            12            34
   5 │   100.0            12            34 
```
