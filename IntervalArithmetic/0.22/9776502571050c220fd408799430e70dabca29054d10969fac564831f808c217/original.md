```
Interval{T<:NumTypes} <: Real
```

Interval type for guaranteed computation with interval arithmetic according to the IEEE Standard 1788-2015. This structure combines a [`BareInterval`](@ref) together with a [`Decoration`](@ref).

Fields:

  * `bareinterval :: BareInterval{T}`
  * `decoration   :: Decoration`
  * `isguaranteed :: Bool`

Constructors compliant with the IEEE Standard 1788-2015:

  * [`interval`](@ref)
  * [`..`](@ref)
  * [`±`](@ref)
  * [`@I_str`](@ref)

See also: [`±`](@ref), [`..`](@ref) and [`@I_str`](@ref).
