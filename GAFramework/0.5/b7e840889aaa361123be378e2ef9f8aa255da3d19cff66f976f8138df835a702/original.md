Fitness function.     fitness(x) is maximized always     To minimize x.objvalue, dispatch fitness(x) to -x.objvalue for your Creature     Recommended to make this either x.objvalue to maximize or -x.objvalue to minimize

```
Since fitness(x) used for selecting the fittest creature, elites, and parents,
all the computationally expensive part of calculating the fitness value should
be implemented in the randcreature method.
```
