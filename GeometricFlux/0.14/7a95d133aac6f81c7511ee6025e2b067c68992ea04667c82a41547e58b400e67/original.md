```
LSPE(fg, f_h, f_e, f_p, k; pe_method=RandomWalkPE)
```

Learnable structural positional encoding layer. `LSPE` layer can be seen as a GNN layer warpped in `WithGraph`.

# Arguments

  * `fg::FeaturedGraph`: A given graoh for positional encoding.
  * `f_h::MessagePassing`: Neural network layer for node update.
  * `f_e`: Neural network layer for edge update.
  * `f_p`: Neural network layer for positional encoding.
  * `k::Int`: Dimension of positional encoding.
  * `pe_method`: Initializer for positional encoding.
