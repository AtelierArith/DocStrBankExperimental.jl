```
struct ExchangeGraph{A}
```

Type representing a directed graph to be used in exchanges, see function [`exchange`](@ref) and [`exchange!`](@ref).

# Properties

  * `snd::A`
  * `rcv::A`

`snd[i]` contains a list of the outgoing neighbors of node `i`. `rcv[i]` contains a list of the incomming neighbors of node `i`. `A` is a vector-like container type.

# Supertype hierarchy

```
ExchangeGraph <: Any
```
