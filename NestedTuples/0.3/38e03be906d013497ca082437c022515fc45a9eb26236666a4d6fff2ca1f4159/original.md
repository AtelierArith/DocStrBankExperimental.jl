```
lazymerge(x::NamedTuple, y::NamedTuple)
```

Create a `LazyMerge` struct that behaves like a recursively merged NamedTuple, but is much faster to construct.

In addition to the usual `getproperty`, this structure supports `get`ting by static keys:

```
(lm::LazyMerge).a == get(lm, static(:a))
```

In some situatiuons, the latter can be much faster.

The original use case for this is to support using named tuples as namespaces, especially in the context of probabilistic programming. There, it's common to have one (possibly nested) named tuple for observed data, and another for a proposal in an MCMC algorithm. The merge is therefore in the body of a loop that's executed many times.
