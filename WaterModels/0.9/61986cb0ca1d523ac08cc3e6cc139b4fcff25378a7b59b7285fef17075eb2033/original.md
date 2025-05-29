```
variable_head(
    wm::AbstractWaterModel;
    nw::Int=nw_id_default,
    bounded::Bool=true,
    report::Bool=true
)
```

Instantiates bounded (by default) or unbounded total hydraulic head (or head) variables for nodes in the network at subnetwork (or time) index `nw`, i.e., `h[i]` for `i` in `node`. Also instantiates JuMP expressions that are affine expressions of each head, i.e., pressure, which is computed as `p[i] = h[i] - elevation[i]`, and tank volume (at each tank attached to a node), which is computed as `V[k] = 0.25 * pi * diameter[k]^2 * (h[i] - elevation[i])`, where `k` is the index of the tank; `diameter[k]` is the cross-sectional diameter of the (cylindrical) tank; and `i` is the index of the node to which the tank is attached.
