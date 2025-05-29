```
@outputs(args...)
```

Convert list of user output requests to a vector of functors that generate the requested outputs when applied to a `Result` instance.  In the conversion process, replace lower case letters with upper case.

### Examples

```
julia> output = @outputs FGHz θ ϕ s11db(te,te) S11ang(Te,te)
julia> output = @outputs FGHz theta phi s21db(R,H) ARdB21(H) ARdB11(v)
```
