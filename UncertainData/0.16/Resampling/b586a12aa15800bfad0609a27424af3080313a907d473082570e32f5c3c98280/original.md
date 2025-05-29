```
SequentialResampling{SequentialSamplingConstraint}
```

Indicates that resampling should be done by resampling sequentially.

## Fields

  * `sequential_constraint::SequentialSamplingConstraint`. The sequential sampling constraint,   for example `StrictlyIncreasing()`.

## Examples

```julia
SequentialResampling(StrictlyIncreasing())
```
