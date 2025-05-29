```
compute_probability_vector(θ,τ)
```

# Arguments

  * `θ' : A vector θ = [θ₁,...,θ₅] Hadamard branch parameters.
  * `τ' : A number in {1,2,3,4}, corresonding to the topology of the tree. Here, 1,2,3 correspond to       quartet topologies 13|23, 12|34, and 14|23 respectively, and 4 correspond to the star tree       topology (a four-leaf tree with internal branch length zero.

# Description

Compute the CFN probability model corresponding to the 4-leaf tree with topology τ and branch lengths θ. Uses Formula from Semple and Steel's book on Phylogenetics. See Cor 8.6.6 on p201.

# Examples

`compute*probability*vector([.2,.3,.02,.4,.7],1)'

To display the formulas symbolically, run

`@var θ[1:5]; compute*probability*vector(θ,1)'
