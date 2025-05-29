```
itsample([rng], iter, [wv]; kwargs...)
```

Return a random element of the iterator, optionally specifying a `rng`  (which defaults to `Random.default_rng()`) and a `wv` function. If the iterator is empty, it returns `nothing`.

---

```
itsample([rng], iter, [wv], n::Int; replace = false, ordered = false, kwargs...)
```

Return a vector of `n` random elements of the iterator,  optionally specifying a `rng` (which defaults to `Random.default_rng()`).

`replace` dictates whether sampling is performed with replacement.  `ordered` dictates whether an ordered sample (also called a sequential  sample, i.e. a sample where items appear in the same order as in `iter`).

If the iterator has less than `n` elements, in the case of sampling without replacement, it returns a vector of those elements.
