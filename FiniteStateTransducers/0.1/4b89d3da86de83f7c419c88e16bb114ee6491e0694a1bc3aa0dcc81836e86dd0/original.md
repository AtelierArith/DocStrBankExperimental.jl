`determinize_fsa(fsa)`

Returns a deterministic finite state acceptor. `fsa` must be an acceptor ([`is_acceptor`](@ref)).

Requires the WFST to be defined in a left distributive and weakly divisible semiring.

See [M. Mohri, F. Pereira, Fernando, M. Riley, Michael "Speech Recognition with Weighted Finite-State Transducers" in Springer Handb. Speech Process. 2008](https://cs.nyu.edu/~mohri/pub/hbka.pdf) for details.
