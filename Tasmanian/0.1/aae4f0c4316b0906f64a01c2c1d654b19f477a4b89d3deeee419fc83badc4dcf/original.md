```
makeSequenceGrid!(tsg::TasmanianSG; type, rule, anisotropic_weights=Vector{Int32}(undef, 0), level_limits=Vector{Int32}(undef, 0))
```

creates a new sparse grid using a sequence rule discards any existing grid held by this class

type: string identifying the tensor selection strategy       'level'     'curved'     'hyperbolic'     'tensor'       'iptotal'   'ipcurved'   'iphyperbolic'   'iptensor'       'qptotal'   'qpcurved'   'qphyperbolic'   'qptensor'

rule: string (defines the 1-D rule that induces the grid)       'leja'       'rleja'      'rleja-shifted'       'max-lebesgue'   'min-lebesgue'   'min-delta'

anisotropic_weights: list or array of weights                      length must be `tsg.dimensions` or `2*tsg.dimensions`                      the first `tsg.dimensions` weights must be positive                      see the manual for details
