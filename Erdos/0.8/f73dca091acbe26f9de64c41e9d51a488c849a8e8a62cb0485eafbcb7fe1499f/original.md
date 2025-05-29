```
random_bipartite_configuration_model(
                                n1::Int, n2::Int, 
                                k1::Vector{Int}, k2::Vector{Int}, 
                                G=Graph; seed=-1)
```

Create a random bipartie undirected graph according to the [configuration model](http://tuvalu.santafe.edu/~aaronc/courses/5352/fall2013/csci5352_2013_L11.pdf). It contains `n1+n2` vertices. The vertex `i` in the first set will have degree `k1[i]`, while the vertex `i` in the second set will have degree `k2[i]`.

`G` is the resulting graph type.
