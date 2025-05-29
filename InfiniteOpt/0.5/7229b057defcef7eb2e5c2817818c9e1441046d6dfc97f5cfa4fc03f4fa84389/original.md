```
DiscreteMeasureData{P <: Union{JuMP.AbstractVariableRef,
                    Vector{<:JuMP.AbstractVariableRef}},
                    N, B <: Union{Float64, Vector{Float64}},
                    F <: Function
                    } <: AbstractMeasureData
```

A DataType for immutable measure abstraction data where the abstraction is of the form: $measure = \int_{\tau \in T} f(\tau) w(\tau) d\tau \approx \sum_{i = 1}^N \alpha_i f(\tau_i) w(\tau_i)$. The supports and coefficients are immutable (i.e., they will not change even if supports are changed for the underlying infinite parameter.) This type can be used for both 1-dimensional and multi-dimensional measures.

**Fields**

  * `parameter_refs::P`: The infinite parameter(s) over which the integration occurs.                      These can be comprised of multiple independent parameters,                      but dependent parameters cannot be mixed with other types.
  * `coefficients::Vector{Float64}`: Coefficients $\alpha_i$ for the above                                  measure abstraction.
  * `supports::Array{Float64, N}`: Supports points $\tau_i$. This is a `Vector`                                if only one parameter is given, otherwise it is                                a `Matrix` where the supports are stored column-wise.
  * `label::DataType`: Label for the support points $\tau_i$ when stored in the                  infinite parameter(s), stemming from [`AbstractSupportLabel`](@ref).
  * `weight_function::F`: Weighting function $w$ must map an individual                              support value to a `Real` scalar value.
  * `lower_bounds::B`: Lower bound in accordance with $T$, this denotes the                   intended interval of the measure and should be `NaN` if ignored
  * `upper_bounds::B`: Same as above but the upper bound.
  * `is_expect::Bool`: Is this data associated with an expectation call?
