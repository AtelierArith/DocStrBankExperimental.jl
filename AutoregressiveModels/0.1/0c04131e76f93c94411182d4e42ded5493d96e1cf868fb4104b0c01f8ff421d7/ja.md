```
impulse(var::VARProcess, ε0::AbstractVecOrMat, nhorz::Integer; kwargs...)
impulse(var::VARProcess, ishock::Union{Integer, AbstractRange}, nhorz::Integer; kwargs...)
```

[`impulse!`](@ref)と同様ですが、結果を保存するための配列を割り当てます。ホライズンの数は`nhorz`で明示的に指定する必要があります。
