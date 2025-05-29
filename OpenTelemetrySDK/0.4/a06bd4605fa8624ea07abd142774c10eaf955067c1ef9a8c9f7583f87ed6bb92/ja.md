```
TracerProvider(;kw...)
```

# キーワード引数

  * `sampler`::[`AbstractSampler`](@ref)=[`DEFAULT_ON`](@ref)
  * `resource`=[`Resource`](@ref)()
  * `span_processor`::[`AbstractSpanProcessor`](@ref)=[`SimpleSpanProcessor`](@ref)([`ConsoleExporter`](@ref))
  * `id_generator`::[`AbstractIdGenerator`](@ref)=[`RandomIdGenerator`](@ref)()
  * `limit_info`=[`LimitInfo`](@ref)()

[`AbstractTracerProvider`](@ref)で定義されているものを超えて、以下の追加メソッドが提供されています：

  * [`flush(p::TracerProvider)`](@ref)
  * [`close(p::TracerProvider)`](@ref)
  * [`Base.push!(p::TracerProvider, sp::AbstractSpanProcessor)`](@ref)
