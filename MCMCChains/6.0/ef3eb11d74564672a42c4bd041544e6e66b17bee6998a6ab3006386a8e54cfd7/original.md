```
sample([rng,] chn::Chains, [wv::AbstractWeights,] n; replace=true, ordered=false)
```

Sample `n` samples from the pooled (!) chain `chn`.

The keyword arguments `replace` and `ordered` determine whether sampling is performed with replacement and whether the sample is ordered, respectively. If specified, sampling probabilities are proportional to weights `wv`.

!!! note
    If `chn` contains multiple chains, they are pooled (i.e., appended) before sampling. This ensures that even in this case exactly `n` samples are returned:

    ```jldoctest
    julia> chn = Chains(randn(11, 4, 3));

    julia> size(sample(chn, 7)) == (7, 4, 1)
    true
    ```

