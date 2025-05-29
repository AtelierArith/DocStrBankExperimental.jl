```
@non_trainable(x)
```

Mark a value as non-trainable. This bypasses the regular checks and places the value into the state of the layer.

## Arguments

  * `x`: The value to be marked as non-trainable.

## Examples

```jldoctest
julia> using Lux, Random

julia> r = @compact(w=ones(3), w_fixed=@non_trainable(rand(3))) do x
           @return sum(w .* x .+ w_fixed)
       end;

julia> ps, st = Lux.setup(Xoshiro(0), r);

julia> size(ps.w)
(3,)

julia> size(st.w_fixed)
(3,)

julia> res, st_ = r([1, 2, 3], ps, st);

julia> st_.w_fixed == st.w_fixed
true

julia> res isa Number
true
```
