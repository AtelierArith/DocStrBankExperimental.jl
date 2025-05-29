```
filter(data::PopData, args...)
```

A drop-in replacement for the DataFrames.filter! where `PopData` is the first argument and the filtering conditions are the second argument. Mutates the  `PopData` in place and returns it. **Note** the argument order is opposite of that from DataFrames.jl.

**Example**

```
x = @nancycats ;

filter!(x, :name => i -> i ∈ samplenames(x)[1:10]) ;

show(x)
PopData{Diploid, 9 Microsatellite loci}
  Samples: 10
  Populations: 1
```
