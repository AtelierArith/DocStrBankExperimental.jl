Vulkanの型を対応するJuliaの型に変換します。

### 例

```jldoctest
julia> from_vk(VersionNumber, UInt32(VkCore.VK_MAKE_VERSION(1, 2, 3)))
v"1.2.3"

julia> from_vk(String, (0x68, 0x65, 0x6c, 0x6c, 0x6f, 0x00))
"hello"

julia> from_vk(Bool, UInt32(1))
true
```

```julia
from_vk(T, x)
```

は[`packages/Vulkan/qhpzm/src/prewrap/conversions.jl:39`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/prewrap/conversions.jl)で定義されています。

```julia
from_vk(T, x)
```

は[`packages/Vulkan/qhpzm/src/prewrap/conversions.jl:40`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/prewrap/conversions.jl)で定義されています。

```julia
from_vk(T, x, next_types)
```

は[`packages/Vulkan/qhpzm/src/prewrap/conversions.jl:41`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/prewrap/conversions.jl)で定義されています。

```julia
from_vk(T, x)
```

は[`packages/Vulkan/qhpzm/src/prewrap/conversions.jl:42`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/prewrap/conversions.jl)で定義されています。

```julia
from_vk(T, x)
```

は[`packages/Vulkan/qhpzm/src/prewrap/conversions.jl:43`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/prewrap/conversions.jl)で定義されています。

```julia
from_vk(T, version)
```

は[`packages/Vulkan/qhpzm/src/prewrap/conversions.jl:44`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/prewrap/conversions.jl)で定義されています。

```julia
from_vk(T, str)
```

は[`packages/Vulkan/qhpzm/src/prewrap/conversions.jl:46`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/prewrap/conversions.jl)で定義されています。
