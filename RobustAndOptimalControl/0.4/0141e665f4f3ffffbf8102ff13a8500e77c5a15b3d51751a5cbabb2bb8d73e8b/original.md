```
G = feedback_control(P, K)
```

Return the (negative feedback) closed-loop system from input of `K` to output of `P` while outputing also the control signal (output of `K`), i.e., `G` maps references to `[y; u]`

# Example:

The following are two equivalent ways of achieving the same thing

```julia
G = ssrand(3,4,2)
K = ssrand(4,3,2)

Gcl1 = feedback_control(G, K) # First option

# Second option using named systems and connect
G = named_ss(G, :G)
K = named_ss(K, :K)
S = sumblock("Ku = r - Gy", n=3) # Create a sumblock that computes r - Gy for vectors of length 3

z1 = [G.y; K.y] # Output both plant and controller outputs
w1 = :r^3       # Extenal inputs are the three references into the sum block
connections = [K.y .=> G.u; G.y .=> G.y; K.u .=> K.u] # Since the sumblock uses the same names as the IO signals of G,K, we can reuse these names here
Gcl2 = connect([G, K, S], connections; z1, w1)

@test linfnorm(minreal(Gcl1 - Gcl2.sys))[1] < 1e-10 # They are the same
```

To include also an input disturbance, use

```
Gcl = feedback(K, P, W2=:, Z2=:, Zperm=[(1:ny).+nu; 1:nu]) # y,u from r,d
```

See also [`extended_gangoffour`](@ref).
