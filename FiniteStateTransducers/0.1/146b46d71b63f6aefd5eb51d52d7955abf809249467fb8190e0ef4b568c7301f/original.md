`add_arc!(fst, src, dest, ilabel, olabel[, w=one(W)])`

`add_arc!(fst, srcdest::Pair, ilabelolabel::Pair[, w=one(W)])`

Adds an arc from state `src` to state `dest` with input label `ilabel`, output label `olabel` and weight `w`. Alternative notation utilizes `Pair`s.

If `w` is not provided this defaults to `one(W)` where `W` is the weight type of `fst`.
