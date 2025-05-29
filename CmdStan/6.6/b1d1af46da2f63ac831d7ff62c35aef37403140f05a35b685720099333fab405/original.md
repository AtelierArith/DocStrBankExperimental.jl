# Sample type and constructor

Settings for method=Sample() in Stanmodel. 

### Method

```julia
Sample(;
  num_samples=1000,
  num_warmup=1000,
  save_warmup=false,
  thin=1,
  adapt=CmdStan.Adapt(),
  algorithm=SamplingAlgorithm()
)
```

### Optional arguments

```julia
* `num_samples::Int64`          : Number of sampling iterations ( >= 0 )
* `num_warmup::Int64`           : Number of warmup iterations ( >= 0 )
* `save_warmup::Bool`           : Include warmup samples in output
* `thin::Int64`                 : Period between saved samples
* `adapt::Adapt`                : Warmup adaptation settings
* `algorithm::SamplingAlgorithm`: Sampling algorithm

```

### Related help

```julia
?Stanmodel                      : Create a StanModel
?Adapt
?SamplingAlgorithm
```
