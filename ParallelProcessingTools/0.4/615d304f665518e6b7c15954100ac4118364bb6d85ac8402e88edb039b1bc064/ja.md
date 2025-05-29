```
ThreadLocal{T} <: AbstractThreadLocal{T}
```

スレッドローカル値を表します。APIについては[`AbstractThreadLocal`](@ref)を参照してください。

コンストラクタ:

```julia
ThreadLocal{T}() where {T}
ThreadLocal(value::T) where {T}
ThreadLocal{T}(f::Base.Callable) where {T}
```

例:

```julia
tlvalue = ThreadLocal(0)
@onthreads allthreads() tlvalue[] = Base.Threads.threadid()
getallvalues(tlvalue) == allthreads()
```

```julia
rand_value_on_each_thread = ThreadLocal{Float64}(rand)
all(x -> 0 < x < 1, getallvalues(rand_value_on_each_thread))
```
