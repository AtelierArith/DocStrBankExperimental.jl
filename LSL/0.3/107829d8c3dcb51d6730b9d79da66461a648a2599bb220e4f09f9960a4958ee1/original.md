```
push_sample(outlet::StreamOutlet{T},
            data::Vector{T};
            timestamp = 0.0,
            pushthrough = true)
```

Push a sample into the outlet. Each entry in the vector corresponds to one channel.

# Keyword arguments

-`timestamp::Number`: Capture time of the sample, in agreement with `local_clock()`, if                       ommitted, the current time is used.

  * `passthrough::Bool`: Whether to push the sample through to the receivers instead of                      buffering it with subsequent samples. Note that the chunk_size, if                      specified at outlet construction, takes precedence over the                      pushthrough flag.
