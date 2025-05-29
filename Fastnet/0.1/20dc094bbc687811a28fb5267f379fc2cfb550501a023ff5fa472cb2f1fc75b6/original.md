```
simstep!(sim)
```

Simulate the next event in *sim*.

This function will always advance the sim by exactly one event. If no event is possible it will advance time by one timeunit.   Output is generated at start time and directly after the event has occured. 

See also [FastSim](#Fastnet.FastSim),[simstep](#Fastnet.simstep) 

# Examples

```jldoctest
julia> using Fastnet

julia> net=FastNet(2,1,2,[])
Network of 0 nodes and 0 links

julia> n1=makenode!(net,1);

julia> n2=makenode!(net,2);

julia> function rates!(r,t)
         r[1]=countnodes(net,2)
         end
rates! (generic function with 1 method)

julia> function simpleproc!()
         node=randomnode(net,2)
         nodestate!(net,node,1)
         end
simpleproc! (generic function with 1 method)

julia> sim=FastSim(net,rates!,[simpleproc!]; output=false)
Simulation run, currently at time 0.0

julia> simstep!(sim)

julia> nodecounts(net)
2-element Vector{Int64}:
 2
 0
```
