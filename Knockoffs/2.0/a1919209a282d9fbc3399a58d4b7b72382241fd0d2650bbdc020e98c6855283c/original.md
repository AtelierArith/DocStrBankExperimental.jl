```
simulate_ER(p::Int; [invert])
```

Simulates a covariance matrix from a clustered Erdos-Renyi graph, which is a block diagonal matrix where each block is an Erdo-Renyi graph. The result is scaled back to a correlation matrix. 

For details, see the 4th simulation routine in section 5.1 of Li and Maathius  https://academic.oup.com/jrsssb/article/83/3/534/7056103?login=false

# Inputs

  * `p`: Dimension of covariance matrix
  * `ϕ`: Probability of forming an edge between any 2 nodes
  * `lb`: lower bound for the value of an edge (drawn from uniform distribution)
  * `ub`: upper bound for the value of an edge (drawn from uniform distribution)
  * `invert`: Whther to invert the covariance matrix (to obtain the precision)
  * `λmin`: minimum eigenvalue of the resulting covariance matrix
  * `blocksize`: Number of variables within each ER graph.
