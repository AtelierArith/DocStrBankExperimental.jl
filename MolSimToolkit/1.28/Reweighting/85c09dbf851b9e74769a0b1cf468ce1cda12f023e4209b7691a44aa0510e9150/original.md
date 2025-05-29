```
reweight(
    simulation::Simulation, 
    f_perturbation::Function, 
    group_1::AbstractVector{<:Integer}; 
    cutoff::Real = 12.0, 
    k::Real = 1.0, 
    T::Real = 1.0
)
reweight(
    simulation::Simulation, 
    f_perturbation::Function, 
    group_1::AbstractVector{<:Integer}, 
    group_2::AbstractVector{<:Integer};     
    cutoff::Real = 12.0, 
    k::Real = 1.0, 
    T::Real = 1.0
)
```

Function that calculates the energy difference when a perturbation is applied on the system.

It returns "ReweightResults" structure that contains three results: `probability`, `relative_probability` and `energy` vectors.

The function needs a MolSimToolkit's simulation object, another function to compute the perturbation and one or two types of atoms.

Additionally, you can also define a cutoff distance, the constant "k" (in some cases, it will be Boltzmann constant) and the temperature, T, of the system.

Group*1 (and group*2) is a vector of atoms indexes, extracted, for example, from a pdb file. 

# Example

```julia-repl
julia> import PDBTools

julia> using MolSimToolkit, MolSimToolkit.Resampling

julia> simulation = Simulation("/home/terasaki/.julia/packages/MolSimToolkit/do5dn/src/Reweighting/test/Testing_reweighting.pdb", "//home/terasaki/.julia/packages/MolSimToolkit/do5dn/src/Reweighting/test/Testing_reweighting_10_frames_trajectory.xtc")
Simulation 
    Atom type: Atom
    PDB file: /home/lucasv/.julia/dev/MolSimToolkit/src/Reweighting/test/Testing_reweighting.pdb
    Trajectory file: /home/lucasv/.julia/dev/MolSimToolkit/src/Resampling/test/Testing_reweighting_10_frames_trajectory.xtc
    Total number of frames: 10
    Frame range: 1:1:10
    Number of frames in range: 10
    Current frame: nothing

julia> i1 = PDBTools.selindex(atoms(simulation), "index 97 or index 106")
2-element AbstractVector{<:Integer}:
  97
 106

julia> i2 = PDBTools.selindex(atoms(simulation), "residue 15 and name HB3")
1-element AbstractVector{<:Integer}:
 171

julia> sum_of_dist = reweight(simulation, (i,j,d2) -> d2, i1, i2; cutoff = 25.0)
-------------
FRAME WEIGHTS
-------------

Average probability = 0.1
standard deviation = 0.011364584999859616

-------------------------------------------
FRAME WEIGHTS RELATIVE TO THE ORIGINAL ONES
-------------------------------------------

Average probability = 0.6001821184861403
standard deviation = 0.06820820700931557

----------------------------------
COMPUTED ENERGY AFTER PERTURBATION
----------------------------------

Average energy = 0.5163045415662408
standard deviation = 0.11331912115883522

julia> sum_of_dist.energy
10-element Vector{Real}:
 17.738965476707595
 15.923698293115915
 17.16614676290554
 19.33003841107648
 16.02329229247863
 19.639005665480983
 35.73986006775934
 21.88798265022823
 20.66180657974777
 16.845109623700647

This result is the energy difference between the  perturbed frame and the original one. In this case, it is the sum of distances between the reffered atoms
```
