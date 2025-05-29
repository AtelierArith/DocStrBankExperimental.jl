```
EvalOptions
```

This holds options for expression evaluation, such as evaluation backend.

# Fields

  * `turbo::Val{T}=Val(false)`: If `Val{true}`, use LoopVectorization.jl for faster   evaluation.
  * `bumper::Val{B}=Val(false)`: If `Val{true}`, use Bumper.jl for faster evaluation.
  * `early_exit::Val{E}=Val(true)`: If `Val{true}`, any element of any step becoming   `NaN` or `Inf` will terminate the computation. For `eval_tree_array`, this will   result in the second return value, the completion flag, being `false`. For    calling an expression using `tree(X)`, this will result in `NaN`s filling   the entire buffer. This early exit is performed to avoid wasting compute cycles.   Setting `Val{false}` will continue the computation as usual and thus result in   `NaN`s only in the elements that actually have `NaN`s.
  * `buffer::Union{ArrayBuffer,Nothing}`: If not `nothing`, use this buffer for evaluation.   This should be an instance of `ArrayBuffer` which has an `array` field and an   `index` field used to iterate which buffer slot to use.
