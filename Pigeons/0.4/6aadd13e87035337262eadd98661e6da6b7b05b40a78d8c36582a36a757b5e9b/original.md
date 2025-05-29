```julia
process_sample(processor, exec_folder, round)

```

Process samples that were saved to disk using the `disk` recorder, at the given `round`.

Each sample is passed to the `processor` function, by calling `processor(chain_index, scan_index, sample)` where `chain_index` is the index of the target chain (in classical parallel tempering, there is only one chain at target temperature, so in that case it can be ignored, but it will be non-trivial in e.g. stabilized variational parallel tempering), `scan_index` is the iteration index within the round, starting at 1, and sample is the deserialized sample.

This iterates over the samples in increasing order, looping over `chain_index` in the outer loop and `scan_index` in the inner loop.
