```
itsample([rng], iter, method = AlgRSWRSKIP())
itsample([rng], iter, wfunc, method = AlgWRSWRSKIP())
```

Return a random element of the iterator, optionally specifying a `rng`  (which defaults to `Random.default_rng()`) and a function `wfunc` which accept each element as input and outputs the corresponding weight. If the iterator is empty, it returns `nothing`.

---

```
itsample([rng], iter, n::Int, method = AlgL(); ordered = false)
itsample([rng], iter, wfunc, n::Int, method = AlgAExpJ(); ordered = false)
```

Return a vector of `n` random elements of the iterator,  optionally specifying a `rng` (which defaults to `Random.default_rng()`) a weight function `wfunc` and a `method`. `ordered` dictates whether an  ordered sample (also called a sequential sample, i.e. a sample where items  appear in the same order as in `iter`) must be collected.

If the iterator has less than `n` elements, in the case of sampling without replacement, it returns a vector of those elements.

---

```
itsample(rngs, iters, n::Int)
itsample(rngs, iters, wfuncs, n::Int)
```

Parallel implementation which returns a sample with replacement of size `n` from the multiple iterables. All the arguments except from `n` must be tuples.
