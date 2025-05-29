Convert a type into its corresponding Vulkan type.

### Examples

```jldoctest
julia> to_vk(UInt32, v"1")
0x00400000

julia> to_vk(NTuple{6, UInt8}, "hello")
(0x68, 0x65, 0x6c, 0x6c, 0x6f, 0x00)
```

```julia
to_vk(T, x)
```

defined at [`packages/Vulkan/qhpzm/src/prewrap/conversions.jl:15`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/prewrap/conversions.jl).

```julia
to_vk(_, x)
```

defined at [`packages/Vulkan/qhpzm/src/prewrap/conversions.jl:16`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/prewrap/conversions.jl).

```julia
to_vk(_, x)
```

defined at [`packages/Vulkan/qhpzm/src/prewrap/conversions.jl:17`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/prewrap/conversions.jl).

```julia
to_vk(T, x)
```

defined at [`packages/Vulkan/qhpzm/src/prewrap/conversions.jl:18`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/prewrap/conversions.jl).

```julia
to_vk(T, version)
```

defined at [`packages/Vulkan/qhpzm/src/prewrap/conversions.jl:19`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/prewrap/conversions.jl).

```julia
to_vk(T, s)
```

defined at [`packages/Vulkan/qhpzm/src/prewrap/conversions.jl:20`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/prewrap/conversions.jl).
