```
makeFourierGrid!(tsg::TasmanianSG; type, anisotropic_weights=Vector{Int32}(undef, 0), level_limits=Vector{Int32}(undef, 0))
```

creates a new sparse grid using a Fourier rule discards any existing grid held by this class

type: string identifying the tensor selection strategy       'level'     'curved'     'hyperbolic'     'tensor'       'iptotal'   'ipcurved'   'iphyperbolic'   'iptensor'       'qptotal'   'qpcurved'   'qphyperbolic'   'qptensor'

anisotropic_weights: list or array of weights                      length must be iDimension or 2*iDimension                      the first tsg.dimensions weights must be positive                      see the manual for details
