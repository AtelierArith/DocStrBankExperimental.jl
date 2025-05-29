```julia
randElliptic(d, n; r , diag, norm) 

randElliptic(n; r, norm)
```

  * `d` : default `Normal()`, entry distribution
  * `n`  : dimensions
  * `r` : default `0.5`, the correlation of $H_{ij},H_{ji}$ pairs
  * `norm` : default `false`, if `norm` set to `true`, then the matrix will be normalized with $n^{-1/2}$.
  * `diag` : default `diag=d`, the distribution for diagonal entries.

# Examples

Generate a random elliptic matrix, with entries from $\mathscr{N}(0,1)$ and $\rho(H_{ij},H_{ji})=0.5$ 

```julia
randElliptic(500)

500×500 Matrix{Float64}:
  2.03417    -0.424289    1.28267   …  -0.114754  -1.96059
  0.44479    -1.45563     1.32828       1.00149    0.45786
  1.56525     0.0832211  -0.186738     -1.3914     1.04151
 -0.11633    -0.483301   -1.81348      -1.57536    0.514818
  ⋮                                 ⋱
  1.24274    -0.411623   -1.04984      -0.812778  -1.84479
 -0.0817287  -0.254886    0.674914      0.756269  -0.0296209
 -1.48281     0.51675    -1.58041       0.156923   0.244599
  0.852339    1.04593    -0.119082      1.43634    0.114493
```

Generate a normalized random elliptic matrix, with entries `Poisson(10)` and $\rho(H_{ij},H_{ji})=0.1$ 

```julia
using Distributions
randElliptic(Poisson(10),500, r=0.1 , norm=true)

500×500 Matrix{Float64}:
  0.268328    -0.0413153  -0.0175096   …   0.0190835   0.0201304       
 -0.00599949   0.447214   -0.0175878       0.0112805   0.100704        
 -0.0258879    0.0219927   0.402492       -0.04749    -0.050853        
  0.0219071    0.0119609  -0.00448502      0.0043233   0.0404757       
  ⋮                                    ⋱
 -0.0145467    0.0800297   0.00247891      0.0189267   0.071565        
  0.016412     0.0334019   0.0663348      -0.0180889   0.023773        
 -0.0485914   -0.0575288  -0.0409827       0.491935   -0.0969691       
  0.0405447    0.0503843   0.00624668      0.0558304   0.402492        

```
