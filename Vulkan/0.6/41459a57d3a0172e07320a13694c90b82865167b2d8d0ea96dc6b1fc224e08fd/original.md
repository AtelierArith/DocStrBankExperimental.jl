```
format_type(FORMAT_R4G4_UNORM_PACK8) # UInt8
format_type(FORMAT_R32_SFLOAT) # Float32
format_type(FORMAT_R32G32_SFLOAT) # NTuple{2,Float32}

format_type(FORMAT_R32G32B32_SFLOAT) # RGB{Float32} with the extension for ColorTypes.jl
format_type(FORMAT_R16G16B16A16_SFLOAT) # RGBA{Float16} with the extension for ColorTypes.jl
```

Retrieve a canonical type associated with an uncompressed Vulkan image format.

Note from the spec:

> Depth/stencil formats are considered opaque and need not be stored in the exact number of bits per texel or component ordering indicated by the format enum.


This means we can't reliably interpret an image with a depth/stencil format. The image needs to be transitioned to a color format first (e.g. `D16` to `R16`), and when both depth and stencil aspects are present, a view must be formed for the transfer (e.g. `D16S8` must be viewed with the depth aspect for transfer from `D16` into `R16`, or with the stencil aspect for transfer from `S8` into `R8`).

The exact byte representation is available at https://registry.khronos.org/vulkan/specs/1.3-extensions/html/chap49.html#texel-block-size.

Note from the spec for packed representations:

> Packed formats store multiple components within one underlying type. The bit representation is that the first component specified in the name of the format is in the most-significant bits and the last component specified is in the least-significant bits of the underlying type. The in-memory ordering of bytes comprising the underlying type is determined by the host endianness.


One must therefore be careful about endianness for packed representations when reading from an image.

# Extended help

Here is an informative list of most mappings (the element type, where relevant, is omitted and represented as `T`):

`PACK8`: -> `UInt8`

  * `RG`

`PACK16`: -> `UInt16`

  * `RGBA`
  * `BGRA`
  * `RGB`
  * `BGR`
  * `RGBA1`
  * `BGRA1`
  * `A1RGB`
  * `A4RGB`
  * `A4BGR`
  * `R12X4`

`PACK32`: -> `UInt32`

  * `ARGB`
  * `A2RGB`
  * `A2BGR`
  * `BGR`
  * `EBGR`
  * `X8D24`
  * `GBGR_422`
  * `BGRG_422`

8-bit per component:

  * `R` -> `T`
  * `RG` -> `NTuple{2,T}`
  * `RGB` -> `RGB{T}`
  * `BGR` -> `BGR{T}`
  * `RGBA` -> `RGBA{T}`
  * `BGRA` -> `BGRA{T}`
  * `ABGR` -> `ABGR{T}`
  * `GBGR` -> `NTuple{4,T}`
  * `BGRG` -> `NTuple{4,T}`
  * `S` -> undefined, transition to `R8`

16-bit per component:

  * `R` -> `T`
  * `RG` -> `NTuple{2,T}`
  * `RGB` -> `RGB{T}`
  * `RGBA` -> `RGBA{T}`
  * `D` -> undefined, transition to `R16`

32-bit per component:

  * `R` -> `T`
  * `RG` -> `NTuple{2,T}`
  * `RGB` -> `RGB{T}`
  * `RGBA` -> `RGBA{T}`
  * `D` -> undefined, transition to `R32`

64-bit per component:

  * `R` -> `T`
  * `RG` -> `NTuple{2,T}`
  * `RGB` -> `RGB{T}`
  * `RGBA` -> `RGBA{T}`

Depth/stencil:

  * `D16S8` -> undefined, transition to `R16`/`R8`
  * `D24S8` -> undefined, transition to ?/`R8`
  * `D32S8` -> undefined, transition to `R32`/`R8`

Compressed formats: -> undefined byte representation, transition to other format

  * `BC`
  * `ETC2`
  * `EAC`
  * `ASTC`
  * `PVRTC`

```julia
format_type(x)
```

defined at [`packages/Vulkan/qhpzm/src/formats.jl:100`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl).

```julia
format_type(_)
```

defined at [`packages/Vulkan/qhpzm/src/formats.jl:101`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl).

```julia
format_type(_)
```

defined at [`packages/Vulkan/qhpzm/src/formats.jl:103`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl).

```julia
format_type(_)
```

defined at [`packages/Vulkan/qhpzm/src/formats.jl:104`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl).

```julia
format_type(_)
```

defined at [`packages/Vulkan/qhpzm/src/formats.jl:105`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl).

```julia
format_type(_)
```

defined at [`packages/Vulkan/qhpzm/src/formats.jl:109`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl).

```julia
format_type(_)
```

defined at [`packages/Vulkan/qhpzm/src/formats.jl:110`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl).

```julia
format_type(_)
```

defined at [`packages/Vulkan/qhpzm/src/formats.jl:111`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl).

```julia
format_type(_)
```

defined at [`packages/Vulkan/qhpzm/src/formats.jl:112`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl).

```julia
format_type(_)
```

defined at [`packages/Vulkan/qhpzm/src/formats.jl:113`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl).

```julia
format_type(_)
```

defined at [`packages/Vulkan/qhpzm/src/formats.jl:114`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl).

```julia
format_type(_)
```

defined at [`packages/Vulkan/qhpzm/src/formats.jl:115`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl).

```julia
format_type(_)
```

defined at [`packages/Vulkan/qhpzm/src/formats.jl:116`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl).

```julia
format_type(_)
```

defined at [`packages/Vulkan/qhpzm/src/formats.jl:117`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl).

```julia
format_type(_)
```

defined at [`packages/Vulkan/qhpzm/src/formats.jl:118`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl).

```julia
format_type(_)
```

defined at [`packages/Vulkan/qhpzm/src/formats.jl:119`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl).

```julia
format_type(_)
```

defined at [`packages/Vulkan/qhpzm/src/formats.jl:120`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl).

```julia
format_type(_)
```

defined at [`packages/Vulkan/qhpzm/src/formats.jl:121`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl).

```julia
format_type(_)
```

defined at [`packages/Vulkan/qhpzm/src/formats.jl:122`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl).

```julia
format_type(_)
```

defined at [`packages/Vulkan/qhpzm/src/formats.jl:123`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl).

```julia
format_type(_)
```

defined at [`packages/Vulkan/qhpzm/src/formats.jl:124`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl).

```julia
format_type(_)
```

defined at [`packages/Vulkan/qhpzm/src/formats.jl:125`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl).

```julia
format_type(_)
```

defined at [`packages/Vulkan/qhpzm/src/formats.jl:126`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl).

```julia
format_type(_)
```

defined at [`packages/Vulkan/qhpzm/src/formats.jl:127`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl).

```julia
format_type(_)
```

defined at [`packages/Vulkan/qhpzm/src/formats.jl:128`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl).

```julia
format_type(_)
```

defined at [`packages/Vulkan/qhpzm/src/formats.jl:129`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl).

```julia
format_type(_)
```

defined at [`packages/Vulkan/qhpzm/src/formats.jl:130`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl).

```julia
format_type(_)
```

defined at [`packages/Vulkan/qhpzm/src/formats.jl:131`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl).

```julia
format_type(_)
```

defined at [`packages/Vulkan/qhpzm/src/formats.jl:132`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl).

```julia
format_type(_)
```

defined at [`packages/Vulkan/qhpzm/src/formats.jl:133`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl).

```julia
format_type(_)
```

defined at [`packages/Vulkan/qhpzm/src/formats.jl:134`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl).

```julia
format_type(_)
```

defined at [`packages/Vulkan/qhpzm/src/formats.jl:135`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl).

```julia
format_type(_)
```

defined at [`packages/Vulkan/qhpzm/src/formats.jl:136`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl).

```julia
format_type(_)
```

defined at [`packages/Vulkan/qhpzm/src/formats.jl:137`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl).

```julia
format_type(_)
```

defined at [`packages/Vulkan/qhpzm/src/formats.jl:138`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl).

```julia
format_type(_)
```

defined at [`packages/Vulkan/qhpzm/src/formats.jl:139`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl).

```julia
format_type(_)
```

defined at [`packages/Vulkan/qhpzm/src/formats.jl:140`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl).

```julia
format_type(_)
```

defined at [`packages/Vulkan/qhpzm/src/formats.jl:141`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl).

```julia
format_type(_)
```

defined at [`packages/Vulkan/qhpzm/src/formats.jl:142`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl).

```julia
format_type(_)
```

defined at [`packages/Vulkan/qhpzm/src/formats.jl:143`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl).

```julia
format_type(_)
```

defined at [`packages/Vulkan/qhpzm/src/formats.jl:144`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl).

```julia
format_type(_)
```

defined at [`packages/Vulkan/qhpzm/src/formats.jl:145`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl).

```julia
format_type(_)
```

defined at [`packages/Vulkan/qhpzm/src/formats.jl:146`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl).

```julia
format_type(_)
```

defined at [`packages/Vulkan/qhpzm/src/formats.jl:147`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl).

```julia
format_type(_)
```

defined at [`packages/Vulkan/qhpzm/src/formats.jl:148`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl).

```julia
format_type(_)
```

defined at [`packages/Vulkan/qhpzm/src/formats.jl:149`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl).

```julia
format_type(_)
```

defined at [`packages/Vulkan/qhpzm/src/formats.jl:150`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl).

```julia
format_type(_)
```

defined at [`packages/Vulkan/qhpzm/src/formats.jl:151`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl).

```julia
format_type(_)
```

defined at [`packages/Vulkan/qhpzm/src/formats.jl:152`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl).

```julia
format_type(_)
```

defined at [`packages/Vulkan/qhpzm/src/formats.jl:153`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl).

```julia
format_type(_)
```

defined at [`packages/Vulkan/qhpzm/src/formats.jl:154`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl).

```julia
format_type(_)
```

defined at [`packages/Vulkan/qhpzm/src/formats.jl:155`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl).

```julia
format_type(_)
```

defined at [`packages/Vulkan/qhpzm/src/formats.jl:156`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl).

```julia
format_type(_)
```

defined at [`packages/Vulkan/qhpzm/src/formats.jl:157`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl).

```julia
format_type(_)
```

defined at [`packages/Vulkan/qhpzm/src/formats.jl:158`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl).

```julia
format_type(_)
```

defined at [`packages/Vulkan/qhpzm/src/formats.jl:159`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl).

```julia
format_type(_)
```

defined at [`packages/Vulkan/qhpzm/src/formats.jl:160`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl).

```julia
format_type(_)
```

defined at [`packages/Vulkan/qhpzm/src/formats.jl:161`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl).

```julia
format_type(_)
```

defined at [`packages/Vulkan/qhpzm/src/formats.jl:162`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl).

```julia
format_type(_)
```

defined at [`packages/Vulkan/qhpzm/src/formats.jl:171`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl).

```julia
format_type(_)
```

defined at [`packages/Vulkan/qhpzm/src/formats.jl:172`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl).

```julia
format_type(_)
```

defined at [`packages/Vulkan/qhpzm/src/formats.jl:173`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl).
