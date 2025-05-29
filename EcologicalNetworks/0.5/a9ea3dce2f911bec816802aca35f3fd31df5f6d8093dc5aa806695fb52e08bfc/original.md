```
resilience(N::AbstractUnipartiteNetwork)
```

A resilience parameters described by Gao et al. (2016). It is a global parameters describing the dynamics of an unipartite network as an effective 1D equation of the form

f(xeff) = F(xeff) + βeff G(xeff, xeff)

i.e. describing a second-order term representing the effect of the network on the dynamics of the 'effective state' xeff of the system.

> Goa, J., Barzael, B. and Barabási 2016. Universal resilience patterns in complex networks. Nature 530(7590), 307-312. doi:10.1038/nature16948

