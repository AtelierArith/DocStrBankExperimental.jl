```julia
sketch(
    A,
    X;
    force_single_batch,
    batch_size,
    out_dic,
    kwargs...
)

```

Returns the sketch of `X` for the sketching operator `A`.  Unless `force_single_sketch` is set to `true`, the sketch is computed by splitting `X` into smaller batches and sketching each batch individually for memory efficiency. The batch size is selected using `BatchIterators.choose_batchsize`, but in particular the following constraints can be used:

  * `maxmemGB`: maximum memory of a sketched batch;
  * `maxbatchsize`: maximum number of samples of a batch.
  * `batch_size`: exact batch size to use.
  * `force_single_batch`: will sketch all the data as one single batch.
