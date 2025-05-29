```
shownodes(net)
```

Print information on all nodes in FastNet *net*.

This function is mainly intended for testing/debugging. You might want to think twice before  calling it for a large network. Having 10 million nodes printed to your REPL is much less fun than  it sounds. 

See also [showlinks](#Fastnet.showlinks)

# Examples

```jldoctest julia> using Fastnet

julia> net=FastNet(1000,2000,2,[]);

julia> makenodes!(net,5,1)

julia> makenodes!(net,5,2)

julia> shownodes(net) id      state 1       1 2       1 3       1 4       1 5       1 6       2 7       2 8       2 9       2 10      2
