```
DataLoader(
    data,
    batchsize = 1;
    partial = true,
    collate = true,
    buffered = collate,
    parallel = Threads.nthreads() > 1,
    useprimary = false,
)
```

Create an efficient iterator of batches over [data container](../documents/docs/datacontainers.md) `data`.

## Arguments

Positional

  * `data`: A data container supporting the `LearnBase` data access pattern
  * `batchsize = 1`: Number of samples to batch together. Disable batching by setting to `nothing`.

Keyword

  * `partial::Bool = true`: Whether to include the last batch when `nobs(dataset)` is not divisible by `batchsize`. `true` ensures all batches have the same size, but some samples might be dropped.
  * `buffered::Bool = collate`: If `buffered` is `true`, loads data inplace using `getobs!`. See [Data containers](../documents/docs/datacontainers.md) for details on buffered loading.
  * `parallel::Bool = Threads.nthreads() > 1)`: Whether to load data in parallel, keeping the primary thread is. Default is `true` if more than one thread is available.
  * `useprimary::Bool = false`: If `false`, keep the main thread free when loading data in parallel. Is ignored if `parallel` is `false`.

## Examples

Creating a data loader with batch size 16 and iterating over it:

```julia
data = (rand(128, 10000), rand(1, 10000))
dataloader = DataLoader(data, 16)

for (xs, ys) in dataloader
end
```

Creating a data loader that [uses buffers](../documents/docs/inplaceloading.md) to load batches:

```julia
data = rand(100, 64)
dataloader = DataLoader(data, 16, buffered=true)

size(first(dataloader)) == (100, 16)
```

Turning off [collating](../documents/docs/collate.md):

```julia
dataloader = DataLoader(data, 16, collate=false)

# Batches are a vector of observations
length(first(dataloader)) == 16
```
