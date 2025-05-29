```
FastSim(net,rates!,processes;<keyword arguments>)
```

Create a FastSim structure, representing a FastNet simulation run. 

The first argument *net* is a FastNet structure that is be used in the simulation. 

The second argument is the *rates!* function of the simulation. The rates function is a function  that accepts two arguments. The first of these arguments is an MVector{Float64}  (see StaticArrays Documentation for details). The second argument is a the current time in the simulation. 

When the *rates!* function is called it should compute the total rates of at which the different processes  occur in the system, given the current state of the network. The rates functions returns these values by  filling the array that was passed as the first argument. The rates! should not have a return value. 

Note that when rates are time dependent then the rates! function should use the time value passed to it rather  than obtaining a time form the simulation structure. The simulation code assumes that the rates will remain  constant until the next event. This should be harmless in almost all cases but can cause inaccuracy if your  rates depend explicitely on time, the rates are very senstitive to time and events are rare. 

The third argument is a Vector of functions that implements the processes. The processes are functions  without arguments when they are called they should implement effect of the respecive process running once. Note that elemets of the process function vector should be in the same order as the corresponding rates computed by  the *rates!* vector.

FastSim supports a number of optional keyword arguments:

  * saveas : A String specifying the pathname where results should be saved. If unspecified results aren't saved but can be optained using the *results* function.
  * output : a boolean variable that specifies if results should be printed on the console, by default this is true.  Alternatively also an IOStream can be provided to which results should be written.
  * repfunc : This argument can be used to specify an alternative function to generate outputs and store results.  See [custimization](customization.md) for details.

# Examples

```jldoctest
julia> using Fastnet

julia> const Bored=1; const Excited=2;

julia> net=FastNet(1000,5000,2,[LinkType(Excited,Bored,1)]);

julia> randomgraph!(net);

julia> function rates!(rates,t)
         rates[1]=countlinks(net,1)*0.1
         rates[2]=countnodes(net,Excited)*0.2
         rates[3]=countnodes(net,Bored)*0.001
         end;

julia> function excitement_spreads()
         link=randomlink(net,1)
         nodestate!(net,linkdst(net,link),Excited)
         end;

julia> function get_bored()
         node=randomnode(net,Excited)
         nodestate!(net,node,Bored)
         end;

julia> function great_idea()
         node=randomnode(net,Bored)
         nodestate!(net,node,Excited)
         end;

julia> sim=FastSim(net,rates!,[excitement_spreads,get_bored,great_idea])
Simulation run, currently at time 0.0
```
