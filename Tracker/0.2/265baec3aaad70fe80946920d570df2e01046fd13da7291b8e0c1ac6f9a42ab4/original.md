```
withgradient(f, xs...)
```

This computes the value `f(xs...)` and the gradient with respect to `xs`. However, it differs from `gradient` in several other respects:

  * It will recurse into `xs` using `fmap`, and thus like Zygote's "explicit mode" it returns a tree-like gradient matching the shape of a Flux model. This recursion obeys restrictions imposed by `Optimisers.trainable`, if defined.
  * Only objects satisfying `Optimisers.isnumeric` are regarded as parameters, thus in particular arrays of integers are ignored.
  * Returns plain arrays, not tracked. Uses `nothing` as a strong zero gradient, like Zygote.
  * Allows you to capture auxillary outputs, in addition to the scalar used by `gradient`. To do this, `f` must return a Tuple or NamedTuple. Then it calculates `grad = gradient(first∘f, args...) but returns the whole`val = f(args...)`:

# Examples

```
julia> nt = (vec = [1.0, 2.0], mat = [4.0;;], fun = sin);

julia> withgradient(nt, 2) do x, p
         sum(abs2, x.vec) ^ p
       end
(val = 25.0, grad = ((vec = [20.0, 40.0], mat = [0.0;;], fun = nothing), nothing))

julia> using Flux

julia> model = Chain(Dense(2 => 1, tanh), Dense(1 => 1, bias=false));

julia> withgradient(model, rand(Float32, 2)) do m, x
         sum(abs2, m(x))
       end
(val = 0.035716165f0, grad = ((layers = ((weight = Float32[-0.4241869 -0.16741231], bias = Float32[-0.5529184], σ = nothing), (weight = Float32[-0.04804218;;], bias = nothing, σ = nothing)),), Float32[0.12706584, -0.08858479]))
```
