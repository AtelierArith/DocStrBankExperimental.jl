```
BPELearner(tokenization::AbstractTokenization; min_freq = 10, endsym = "</w>", sepsym = nothing)
```

Construct a learner with a `tokenization` which has `BPETokenization` and `NoBPE` inside.

```
(bper::BPELearner)(word_counts, n_merge)
```

Calling the learner on a `word_counts` dictionary (created by [`count_words`](@ref)) generate a new `tokenization`   where `NoBPE` is replaced with the learned `BPE`.
