```
sizeof_samples(x, duration::Period)
```

Returns the expected size (in bytes) of an encoded `Samples` object corresponding to `x` and `duration`:

```
sample_count(x, duration) * channel_count(x) * sizeof(x.sample_type)
```
