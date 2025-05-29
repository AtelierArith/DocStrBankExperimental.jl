```
struct FermionBath <: AbstractBath
```

An object which describes the interaction between system and fermionic bath

# Fields

  * `bath` : the different fermion-bath-type objects which describes the interaction
  * `op` : The system "emission" operator according to the system-fermionic-bath interaction.
  * `Nterm` : the total number of different bath terms.
  * `δ` : The approximation discrepancy which is used for adding the terminator to HEOM matrix (see function: addTerminator)

# Methods

One can obtain the $k$-th term from `bath::FermionBath` by calling : `bath[k]`. `HierarchicalEOM.jl` also supports the following calls (methods) :

```julia
bath[1:k];   # returns a vector which contains the `1`-st to the `k`-th term.
bath[1:end]; # returns a vector which contains all terms
bath[:];     # returns a vector which contains all terms
from b in bath
    # do something
end
```
