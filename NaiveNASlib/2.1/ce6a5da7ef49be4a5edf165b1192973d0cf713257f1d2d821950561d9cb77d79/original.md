```
Δnout!([utilityfun], v, Δ...)
Δnout!([utilityfun], v1 => Δ1, v2 => Δ2,...)
Δnout!([utilityfun], Δs::AbstractDict)
```

Change output size of all provided vertices with the associated `Δ` and make the appropriate changes to other vertices so that the graph is aligned w.r.t activations. Return `true` if successful (`false` if not successful).

For `Δ`s provided as integers it must be possible to change the size by exactly `Δ` or else the attempt will be considered failed. A failed attempt will be retried immediately in relaxed form where the wanted size changes are moved to the objective. The relaxation means that output size might not change by exactly `Δ`. Use [`relaxed(Δ)`](@ref) to indicate that a size change is  relaxed in the initial attempt. 

Argument `utilityfun` provides a vector `utility = utilityfun(vx)` for any vertex `vx` in the same graph as `v` where  `utility[i] > utility[j]` indicates that output neuron index `i` shall be preferred over `j` for vertex `vx`. It may also provide a scalar which will be used as utility of all neurons of `vx`. If not provided, [`defaultutility(vx)`](@ref) will be used.

Note that `Δnout!([utilityfun], args...)` is equivalent to `Δsize!([utilityfun], ΔNout(args...))`.

### Examples

```jldoctest
julia> using NaiveNASlib, NaiveNASlib.Extend, NaiveNASlib.Advanced

julia> module TestNNLib
           using NaiveNASlib, NaiveNASlib.Extend
           mutable struct Affine{T} W::Matrix{T} end
           NaiveNASlib.nout(a::Affine) = size(a.W, 1)
           NaiveNASlib.nin(a::Affine) = [size(a.W, 2)]
           NaiveNASlib.Δsize!(a::Affine, ins::AbstractVector, outs::AbstractVector) = a.W = parselect(a.W, 2=>ins[1], 1=>outs)
           affine(in, outsize) = absorbvertex(Affine(ones(outsize, nout(in))), in)
           export affine
       end;

julia> using .TestNNLib;

julia> iv = affine(inputvertex("in", 3), 6);

julia> v1 = affine(iv, 4);

julia> v2 = affine(iv, 5);

julia> Δnout!(v1, 3);

julia> Δnout!(v1 => -3, v2 => -2);

julia> Δnout!(Dict(v1 => 3, v2 => 2));

julia> Δnout!(v1, relaxed(2));

julia> Δnout!(v1 => relaxed(2), v2 => -1) do v
           randn(nout(v))
       end;
```
