```
delete!(bn::BayesNets, target::NodeName)
```

Removing cpds will alter the vertex indeces. In particular, removing the ith cpd will swap i and n and then remove n.
