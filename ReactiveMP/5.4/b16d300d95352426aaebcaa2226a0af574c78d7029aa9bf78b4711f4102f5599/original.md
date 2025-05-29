The BIFM node is a node that can be used as a substitution for a state space model. It includes all factor of the time slice to perform efficient inference. This node needs to be used in conjuction with the BIFMHelper node for efficient inference.

```julia
out ~ BIFM(in, zprev, znext)
```

Interfaces:

1. out - latent output (observation) of the BIFM node
2. in - latent input of the BIFM node
3. zprev - previous latent state of the BIFM node
4. znext - next latent state of the BIFM node

*Note: When performing inference, first subscribe to the marginals (in the order: z, out, in) and then to the free energy score function.*

## Example

```julia
# set priors
z_prior ~ MvNormalMeanPrecision(zeros(latent_dim), diagm(ones(latent_dim)))
z_tmp   ~ BIFMHelper(z_prior)

# update last/previous hidden state
z_prev = z_tmp

# loop through observations
for i in 1:nr_samples

    # specify input as random variable
    u[i]   ~ MvNormalMeanPrecision(μu, Wu)

    # specify observation
    xt[i]  ~ BIFM(u[i], z_prev, z[i]) where { meta = BIFMMeta(A, B, C) }
    x[i]   ~ MvNormalMeanPrecision(xt[i], Wx)
    
    # update last/previous hidden state
    z_prev = z[i]

end
```
