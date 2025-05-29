```
MCSBootLowRAM(data ; alpha::Float64=0.05, kwargs...)
```

Method type for doing an MCS test using a dependent bootstrap. This method type has an identical constructor arguments to MCSBoot, so use ?MCSBoot for more detail.

WARNING: This method corresponds to a MCS algorithm that has double the runtime of MCSBoot, but uses about half as much RAM. The vast majority of users will want to use MCSBoot.

WARNING: Results from MCSBootLowRAM are not guaranteed to be identical to those from MCSBoot in finite sample, although they are very likely to both recommend the same set of models in the model confidence set.
