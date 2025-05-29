```
SimplifiedJunDa()
```

A character frequency [dataset](https://lingua.mtsu.edu/chinese-computing/)  of modern Chinese compiled by Jun Da, simplified single-character words only.

Currently, only the modern Chinese dataset is fetched; however, in the future, the other lists may also be provided as an option.

## Examples

```julia-repl
julia> charfreq(SimplifiedJunDa())
DataStructures.Accumulator{String,Int64} with 9932 entries:
  "蜷… => 837
  "哇… => 4055
  "湓… => 62
  "滴… => 8104
  "堞… => 74
  "狭… => 6901
  "尚… => 38376
  "懈… => 2893
  ⋮   => ⋮
```

## Licensing/Copyright

The original author maintains full copyright to the character frequency lists, but provides the lists for research and teaching/learning purposes only, no commercial use without permission from  the author. See their full disclaimer and copyright notice [here](https://lingua.mtsu.edu/chinese-computing/copyright.html).
