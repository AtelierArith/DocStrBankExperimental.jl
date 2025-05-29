```
Returns the discretized version of the infinitesimal generator of the Diffusion Process

    𝕋: f ⭌ lim 1/t * E[f(x_t)|x_0=x]
             = μx * ∂f + 0.5 * σx^2 * ∂^2f

defined on the set of functions f such that 
    
    ∂f(x) = 0 

at the border of the state space

The transpose of this operator corresponds to
    
    𝕋': g ⭌ v * g - ∂(μx * g) + 0.5 * ∂^2(σx^2 * g)

defined on the set of functions g such that  
    
    -μx * g(x) + 0.5 * ∂(σx^2 * g) = 0

at the border of state space
```
