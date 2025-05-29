```
GreedyMethod{MT}
GreedyMethod(; α = 0.0, temperature = 0.0, nrepeat=1)
```

The fast but poor greedy optimizer. Input arguments are

```
* `α` is the parameter for the loss function, for pairwise interaction, L = size(out) - α * (size(in1) + size(in2))
* `temperature` is the parameter for sampling, if it is zero, the minimum loss is selected; for non-zero, the loss is selected by the Boltzmann distribution, given by p ~ exp(-loss/temperature).
* `nrepeat` is the number of repeatition, returns the best contraction order.
```
