```
initparticles(bm, nparticles; biased = false)
```

Creates particles for Gibbs sampling in an Boltzmann machine `bm`. (See also: `Particles`)

For Bernoulli distributed nodes, the particles are initialized with Bernoulli(p) distributed values. If `biased == false`, p is 0.5, otherwise the results of applying the sigmoid function to the bias values are used as values for the nodes' individual p's.

Gaussian nodes are sampled from a normal distribution if `biased == false`. If `biased == true` the mean of the Gaussian distribution is shifted by the bias vector and the standard deviation of the nodes is used for sampling.
