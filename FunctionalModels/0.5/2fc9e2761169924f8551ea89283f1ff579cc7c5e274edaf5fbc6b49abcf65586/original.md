A helper Model to connect a branch between two different nodes and specify potential between nodes and the flow between nodes.

See also [RefBranch](#refbranch).

```julia
Branch(n1, n2, v, i)
```

### Arguments

  * `n1` : the positive reference node.
  * `n2` : the negative reference node.
  * `v` : the potential variable between nodes.
  * `i` : the flow variable between nodes.

### Returns

  * The model, consisting of a RefBranch entry for each node and an equation assigning `v` to `n1 - n2`.

### References

This nodal description is based on work by [David Broman](http://web.ict.kth.se/~dbro/). See the following:

  * http://www.eecs.berkeley.edu/Pubs/TechRpts/2012/EECS-2012-173.pdf
  * http://www.bromans.com/software/mkl/mkl-source-1.0.0.zip
  * https://github.com/david-broman/modelyze

### Examples

Here is the definition of an electrical resistor in the standard library:

```julia
function Resistor(n1::ElectricalNode, n2::ElectricalNode, R::Signal)
    i = Current(compatible_values(n1, n2))
    v = Voltage(value(n1) - value(n2))
    [
        Branch(n1, n2, v, i)
        v ~ R .* i
    ]
end
```
