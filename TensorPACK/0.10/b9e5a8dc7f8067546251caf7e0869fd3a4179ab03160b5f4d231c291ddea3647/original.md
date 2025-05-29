TENPACK  (version 1.0)

(made for julia v1.10.4+ (July 22, 2024), see included license)

Code: https://github.com/bakerte/TensorPACK.jl

Documentation: T.E. Baker, "forthcoming"

Funding for this program is graciously provided by:

  * Institut quantique (Université de Sherbrooke)
  * Département de physique, Université de Sherbrooke
  * Canada First Research Excellence Fund (CFREF)
  * Institut Transdisciplinaire d'Information Quantique (INTRIQ)
  * US-UK Fulbright Commission (Bureau of Education and Cultural Affairs from the United States Department of State)
  * Department of Physics, University of York
  * Canada Research Chair in Quantum Computing for Modelling of Molecules and Materials
  * Department of Physics & Astronomy, University of Victoria
  * Department of Chemistry, University of Victoria
  * Faculty of Science, University of Victoria
  * National Science and Engineering Research Council (NSERC)

# Warning:

We recommend not defining `using LinearAlgebra` to avoid conflicts.  Instead, define

```
import LinearAlgebra
```

and define functions as `LinearAlgebra.svd` to use functions from that package.
