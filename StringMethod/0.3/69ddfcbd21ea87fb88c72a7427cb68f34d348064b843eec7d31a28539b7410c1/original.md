`SimplifiedString(∇V, integrate!, reparameterize!, dist, Δt)` -  Set up the simplified string method data structure

### Fields

  * `∇V`   - Gradient of the potential
  * `integrate!` - Integrator for ẋ = - ∇V(x)
  * `reparameterize!` - Choice of reparametrization
  * `dist` - Distance function used in reparametrization and convergence testing
  * `pin` - Boolean for pinning the endpoints of the string
  * `Δt`    - Time step for the integrator
