```
TracerProvider(;kw...)
```

# Keyword Arguments

  * `sampler`::[`AbstractSampler`](@ref)=[`DEFAULT_ON`](@ref)
  * `resource`=[`Resource`](@ref)()
  * `span_processor`::[`AbstractSpanProcessor`](@ref)=[`SimpleSpanProcessor`](@ref)([`ConsoleExporter`](@ref))
  * `id_generator`::[`AbstractIdGenerator`](@ref)=[`RandomIdGenerator`](@ref)()
  * `limit_info`=[`LimitInfo`](@ref)()

The following extra methods are provided beyond those defined in [`AbstractTracerProvider`](@ref):

  * [`flush(p::TracerProvider)`](@ref)
  * [`close(p::TracerProvider)`](@ref)
  * [`Base.push!(p::TracerProvider, sp::AbstractSpanProcessor)`](@ref)
