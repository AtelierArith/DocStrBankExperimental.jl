```
select_b(m3::Mixer_3CH, select_b::Bool)
```

Make input b the active input.

To make channel a the active input call:

```julia
select_b(m3, false)
select_c(m3, false)
```

### Parameters

  * m3::Mixer_3CH: the three-channel mixer
  * select_b: if true, select channel b

### Returns

  * nothing
