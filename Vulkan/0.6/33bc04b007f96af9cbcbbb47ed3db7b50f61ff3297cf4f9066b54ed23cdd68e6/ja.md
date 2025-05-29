型を対応するVulkan型に変換します。

### 例

```jldoctest
julia> to_vk(UInt32, v"1")
0x00400000

julia> to_vk(NTuple{6, UInt8}, "hello")
(0x68, 0x65, 0x6c, 0x6c, 0x6f, 0x00)
```

```julia
to_vk(T, x)
```

は[`packages/Vulkan/qhpzm/src/prewrap/conversions.jl:15`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/prewrap/conversions.jl)で定義されています。

```julia
to_vk(_, x)
```

は[`packages/Vulkan/qhpzm/src/prewrap/conversions.jl:16`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/prewrap/conversions.jl)で定義されています。

```julia
to_vk(_, x)
```

は[`packages/Vulkan/qhpzm/src/prewrap/conversions.jl:17`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/prewrap/conversions.jl)で定義されています。

```julia
to_vk(T, x)
```

は[`packages/Vulkan/qhpzm/src/prewrap/conversions.jl:18`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/prewrap/conversions.jl)で定義されています。

```julia
to_vk(T, version)
```

は[`packages/Vulkan/qhpzm/src/prewrap/conversions.jl:19`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/prewrap/conversions.jl)で定義されています。

```julia
to_vk(T, s)
```

は[`packages/Vulkan/qhpzm/src/prewrap/conversions.jl:20`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/prewrap/conversions.jl)で定義されています。
