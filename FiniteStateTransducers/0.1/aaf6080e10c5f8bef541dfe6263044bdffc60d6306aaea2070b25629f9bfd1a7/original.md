`wfst2tr(fst,Nt; get_label=get_ilabel)`

Returns an array `time2tr` of length `Nt-1`. The `t`-th element of `time2tr` is a dictionary mapping the transition index between input label at time `t` to the input label at time `t+1`.

```julia
julia> using FiniteStateTransducers

julia> H = WFST(["a1","a2","a3"],["a"]);

julia> add_arc!(H,1,2,"a1","a");

julia> add_arc!(H,2,3,"a2","<eps>");

julia> add_arc!(H,2,2,"a2","<eps>");

julia> add_arc!(H,3,4,"a3","<eps>");

julia> add_arc!(H,3,2,"a3","a");

julia> initial!(H,1);

julia> final!(H,4)
WFST #states: 4, #arcs: 5, #isym: 3, #osym: 1
|1/0.0f0|
a1:a/0.0f0 → (2)
(2)
a2:ϵ/0.0f0 → (3)
a2:ϵ/0.0f0 → (2)
(3)
a3:ϵ/0.0f0 → (4)
a3:a/0.0f0 → (2)
((4/0.0f0))


julia> Nt = 10;

julia> time2tr = wfst2tr(H,Nt)
9-element Array{Dict{Int64,Array{Int64,1}},1}:
 Dict(1 => [2])
 Dict(2 => [2, 3])
 Dict(2 => [2, 3],3 => [2])
 Dict(2 => [2, 3],3 => [2])
 Dict(2 => [2, 3],3 => [2])
 Dict(2 => [2, 3],3 => [2])
 Dict(2 => [2, 3],3 => [2])
 Dict(2 => [2],3 => [2])
 Dict(2 => [3])

```
