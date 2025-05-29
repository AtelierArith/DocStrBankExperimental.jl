A special ModelType to specify branch flows into nodes. When the model is flattened, equations are created to zero out branch flows into nodes. 

See also [Branch](#branch).

```julia
RefBranch(n, i) 
```

### Arguments

  * `n` : the reference node.
  * `i` : the flow variable that goes with this node.

### References

This nodal description is based on work by [David Broman](http://web.ict.kth.se/~dbro/). See the following:

  * http://www.eecs.berkeley.edu/Pubs/TechRpts/2012/EECS-2012-173.pdf
  * http://www.bromans.com/software/mkl/mkl-source-1.0.0.zip
  * https://github.com/david-broman/modelyze

[Modelyze](https://github.com/david-broman/modelyze) has both `RefBranch` and `Branch`.

### Examples

Here is an example of RefBranch used in the definition of a HeatCapacitor in the standard library. `hp` is the reference node (a HeatPort aka Temperature), and `Q_flow` is the flow variable.

```julia
function HeatCapacitor(hp::HeatPort, C::Signal)
    Q_flow = HeatFlow(compatible_values(hp))
    [
        RefBranch(hp, Q_flow)
        der(hp) ~ Q_flow ./ C
    ]
end
```

Here is the definition of SignalCurrent from the standard library a model that injects current (a flow variable) between two nodes:

```julia
function SignalCurrent(n1::ElectricalNode, n2::ElectricalNode, I::Signal)  
    [
        RefBranch(n1, I) 
        RefBranch(n2, -I) 
    ]
end
```
