```
Binomial2BernoulliRBM(weights, visbias, hidbias)
```

Encapsulates the parameters of an RBM with 0/1/2-valued, Binomial (n=2) distributed visible nodes, and Bernoulli distributed hidden nodes. This model is equivalent to a BernoulliRBM in which every two visible nodes are connected with the same weights to each hidden node. The states (0,0) / (1,0) / (0,1) / (1,1) of the visible nodes connected with with the same weights translate as states 0 / 1 / 1 / 2 in the Binomial2BernoulliRBM.
