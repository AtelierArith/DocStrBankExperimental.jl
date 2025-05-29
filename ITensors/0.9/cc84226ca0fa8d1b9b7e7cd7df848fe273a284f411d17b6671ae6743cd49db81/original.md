```
ITensor
```

An ITensor is a tensor whose interface is independent of its memory layout. Therefore it is not necessary to know the ordering of an ITensor's indices, only which indices an ITensor has. Operations like contraction and addition of ITensors automatically handle any memory permutations.

# Examples

```julia
julia> i = Index(2, "i")
(dim=2|id=287|"i")

#
# Make an ITensor with random elements:
#
julia> A = random_itensor(i', i)
ITensor ord=2 (dim=2|id=287|"i")' (dim=2|id=287|"i")
NDTensors.Dense{Float64,Array{Float64,1}}

julia> @show A;
A = ITensor ord=2
Dim 1: (dim=2|id=287|"i")'
Dim 2: (dim=2|id=287|"i")
NDTensors.Dense{Float64,Array{Float64,1}}
 2×2
 0.28358594718392427   1.4342219756446355
 1.6620103556283987   -0.40952231269251566

julia> @show inds(A);
inds(A) = ((dim=2|id=287|"i")', (dim=2|id=287|"i"))

#
# Set the i==1, i'==2 element to 1.0:
#
julia> A[i => 1, i' => 2] = 1;

julia> @show A;
A = ITensor ord=2
Dim 1: (dim=2|id=287|"i")'
Dim 2: (dim=2|id=287|"i")
NDTensors.Dense{Float64,Array{Float64,1}}
 2×2
 0.28358594718392427   1.4342219756446355
 1.0                  -0.40952231269251566

julia> @show storage(A);
storage(A) = [0.28358594718392427, 1.0, 1.4342219756446355, -0.40952231269251566]

julia> B = random_itensor(i, i');

julia> @show B;
B = ITensor ord=2
Dim 1: (dim=2|id=287|"i")
Dim 2: (dim=2|id=287|"i")'
NDTensors.Dense{Float64,Array{Float64,1}}
 2×2
 -0.6510816500352691   0.2579101497658179
  0.256266641521826   -0.9464735926768166

#
# Can add or subtract ITensors as long as they
# have the same indices, in any order:
#
julia> @show A + B;
A + B = ITensor ord=2
Dim 1: (dim=2|id=287|"i")'
Dim 2: (dim=2|id=287|"i")
NDTensors.Dense{Float64,Array{Float64,1}}
 2×2
 -0.3674957028513448   1.6904886171664615
  1.2579101497658178  -1.3559959053693322
```
