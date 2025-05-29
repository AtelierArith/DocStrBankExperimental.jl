`closure(fst; star=true)`

Returns a new WFST `cfst` that is the closure of `fst`.  If `fst` transuces `labels` to `olabel` with weight `w`, `cfst` will be able to transduce `repeat(ilabels,n)` to `repeat(olabels,m)` with weight `w^n` for any integer `n`.

If `star` is `true`, `cfst` will transduce the empty string to itself with weight one.
