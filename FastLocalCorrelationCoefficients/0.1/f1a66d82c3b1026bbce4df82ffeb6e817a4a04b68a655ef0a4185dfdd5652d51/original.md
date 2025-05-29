```
  flcc(haystack,needle)
```

Calculate the local (Pearson) correlation coefficients

$\mathrm{lcc}(x,y) = \frac{(x - \mu_x)^T(y - \mu_y)}{\sigma_x \sigma_y}$

between `needle` and all sliding windows of same size within `haystack`.

`flcc` uses the fast Fourier transform to reduce the computational complexity from O($n_H n_N$) to O(($n_H + n_N) log(n_H + n_N)$), where $n_H$ and $n_N$ are the number of elements of the `haystack` and the `needle`, respectively.

`flcc` supports tensors of any dimensions with real or complex entries.

# Examples

Suppose you have a `haystack`, a tensor of reals and a `needle`, a smaller tensor of the same dimensionality that you are are trying to locate in the `haystack`. Note that the `needle` might be scaled and translated.

The position of the maximum element of `LCC` is the best match between the `needle` and a sliding window of `haystack`

```jldoctest
julia> using FastLocalCorrelationCoefficients

julia> haystack = rand(2^10,2^10);

julia> needle = rand(1) .* haystack[42:48, 45:50] .+ rand(1);

julia> c = flcc(haystack,needle);

julia> best_correlated(c)
CartesianIndex(42, 45)
```

When you need to search for many needles of the same size,

```
  haystack = rand(2^20);
  needle1 = rand(1) .* haystack[2:8] .+ rand(1);
  needle2 = rand(1) .* haystack[42:48] .+ rand(1);
  needle3 = rand(1) .* haystack[end-6:end] .+ rand(1);
```

you can preprocess the `haystack` to avoid redundant computations by precomputing all common information. There is no such preprocessing when using the direct method.

```
  precomp = flcc(haystack,size(needle1));

```

Then use it for much faster queries.

```
  best_correlated(flcc(precomp,needle1)) == 2
  best_correlated(flcc(precomp,needle2)) == 42
  best_correlated(flcc(precomp,needle3)) == 2^20-6
```
