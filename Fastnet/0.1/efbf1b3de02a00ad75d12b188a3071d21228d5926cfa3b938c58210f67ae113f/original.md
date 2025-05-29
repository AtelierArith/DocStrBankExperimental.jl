```
runsim!(sim,dur,out=1.0)
```

Run the simulation *sim* for time *dur*, producing out at intervals *out*.

During the simulation the FastSim and its associated FastNet object will  be updated to reflect the current state of the network (though see notes  on the simulation time, [here](#Fastnet.FastSim)).  

This function simulates the FastSim **at least** for a certain time. If there  are still events occuring in the simulation by the end of the simulation run  the simulation will stop directly after the first event that happens after *dur*. So the simulation time will always be greater than *dur*. In general the difference and  the actual simulation time will be tiny, but in case events are extreley rare the simulation may run significantly beyond *dur*. This behaviour is necessary to  avoid a watchdog-paradox artifact when repeatedly starting short runs. 

Output is generated once at the start of the simulation and then at every multiple of out.  For example, if the simulation time is *t=3.12* at the start of the run, *dur=10* and *out=5* then outputs will be generated at times 3.12, 5 and 10. As a result the network will   be left in a state that differs from the statistics in the last output. 

See also [FastSim](#Fastnet.FastSim),[simstep!](#Fastnet.simstep!) 

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

julia> runsim!(sim,100)

julia> nodecounts(net)
2-element Vector{Int64}:
 2
 0
```
