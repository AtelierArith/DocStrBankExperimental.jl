```
convertDomain!(g::GirfEssential)
```

Convert frequency-domain GIRF to time domain and vice versa. Also calculates dependent parameters.

# Arguments

  * g::GirfEssential - The input GirfEssential object; conversion type is determined by g.isFreqDomainGirf

# Outputs

  * g::GirfEssential - Modified GirfEssential object with converted/calculated fields.

This function was created from part of a code package for GIRF computation and application in MATLAB. The package is available under a BSD 3-clause license. Further info see: https://github.com/MRI-gradient/girf Original MATLAB Author:   Johanna Vannesjo (johanna.vannesjo@gmail.com) Copyright (C) 2014 IBT, University of Zurich and ETH Zurich,               2016 FMRIB centre, University of Oxford
