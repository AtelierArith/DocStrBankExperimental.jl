`determinize_fsa(fsa)`

決定性有限状態受理器を返します。`fsa`は受理器でなければなりません（[`is_acceptor`](@ref)）。

WFSTは左分配的かつ弱可除の半環で定義されている必要があります。

詳細については、[M. Mohri, F. Pereira, Fernando, M. Riley, Michael "Speech Recognition with Weighted Finite-State Transducers" in Springer Handb. Speech Process. 2008](https://cs.nyu.edu/~mohri/pub/hbka.pdf)を参照してください。
