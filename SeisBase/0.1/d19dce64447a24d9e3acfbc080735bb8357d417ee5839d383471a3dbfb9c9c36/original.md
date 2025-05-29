```
PZResp([c = c, p = p, z = z])
```

Instrument response with three fields. Optionally, fields can be set with keywords at creation.

| F   | Type                      | Meaning                                  |
|:--- |:------------------------- |:---------------------------------------- |
| a0  | Float32                   | normalization constant. Equivalencies:   |
|     |                           | = DSP.jl Type `ZeroPoleGain`, field `:k` |
|     |                           | = SEED RESP "A0 normalization factor:"   |
|     |                           | = SEED v2.4 Blockette [53], field 7      |
|     |                           | != FDSN station XML v1.1                 |
|     |                           | <Response>                               |
|     |                           | <InstrumentSensitivity>                  |
|     |                           | <Value>                                  |
| f0  | Float32                   | frequency of normalization by a0; NOT    |
|     |                           | always geophone corner frequency         |
| p   | Array{Complex{Float32},1} | Complex poles of transfer function       |
| z   | Array{Complex{Float32},1} | Complex zeroes of transfer function      |

```
PZResp64([c = c, p = p, z = z])
```

As PZResp, but fields use Float64 precision.

```
PZResp(X::Array{Complex{T},2} [, rev=true])
```

Convert X to a PZResp64 (if `T == Float64`) or PZResp (default) object. Assumes format X = [p z], i.e., poles are in X[:,1] and zeros in X[:,2]; specify `rev=true` if the column assignments are X = [z p].

### External References

Seed v2.4 manual, http://www.fdsn.org/pdf/SEEDManual_V2.4.pdf IRIS Resp format, https://ds.iris.edu/ds/nodes/dmc/data/formats/resp/ Julia DSP filter Types, https://juliadsp.github.io/DSP.jl/stable/filters/

See also: `resp_a0!`, `update_resp_a0!`, `DSP.ZeroPoleGain`
