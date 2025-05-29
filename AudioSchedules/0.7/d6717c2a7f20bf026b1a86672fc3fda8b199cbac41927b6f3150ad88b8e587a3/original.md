```
make_series(synthesizer, sample_rate)
```

Return an iterator that will the play the `synthesizer` at `sample_rate` (with frequency units, like `Hz`). The iterator should yield `Float64`s between -1 and 1. Assumes that iterators will never end while they are scheduled.
