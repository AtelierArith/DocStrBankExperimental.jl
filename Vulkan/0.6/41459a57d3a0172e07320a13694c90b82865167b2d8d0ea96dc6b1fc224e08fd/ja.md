```
format_type(FORMAT_R4G4_UNORM_PACK8) # UInt8
format_type(FORMAT_R32_SFLOAT) # Float32
format_type(FORMAT_R32G32_SFLOAT) # NTuple{2,Float32}

format_type(FORMAT_R32G32B32_SFLOAT) # RGB{Float32} with the extension for ColorTypes.jl
format_type(FORMAT_R16G16B16A16_SFLOAT) # RGBA{Float16} with the extension for ColorTypes.jl
```

圧縮されていないVulkan画像フォーマットに関連付けられた標準的な型を取得します。

仕様からの注意:

> 深度/ステンシルフォーマットは不透明と見なされ、フォーマット列挙体によって示される正確なビット数またはコンポーネントの順序で保存する必要はありません。


これは、深度/ステンシルフォーマットの画像を信頼性を持って解釈できないことを意味します。画像は最初にカラー形式に移行する必要があります（例: `D16`から`R16`へ）、深度とステンシルの両方の側面が存在する場合、転送のためにビューを形成する必要があります（例: `D16S8`は、`D16`から`R16`への転送のために深度側面で表示する必要があります、または`S8`から`R8`への転送のためにステンシル側面で表示する必要があります）。

正確なバイト表現は https://registry.khronos.org/vulkan/specs/1.3-extensions/html/chap49.html#texel-block-size で入手できます。

パックされた表現に関する仕様からの注意:

> パックされたフォーマットは、1つの基礎となる型内に複数のコンポーネントを格納します。ビット表現は、フォーマットの名前で指定された最初のコンポーネントが最上位ビットにあり、最後のコンポーネントが基礎となる型の最下位ビットにあるというものです。基礎となる型を構成するバイトのメモリ内の順序は、ホストのエンディアンによって決まります。


したがって、画像から読み取る際には、パックされた表現のエンディアンに注意する必要があります。

# 拡張ヘルプ

以下は、ほとんどのマッピングの情報リストです（関連する場合、要素型は省略され、`T`として表されます）:

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

8ビット/コンポーネント:

  * `R` -> `T`
  * `RG` -> `NTuple{2,T}`
  * `RGB` -> `RGB{T}`
  * `BGR` -> `BGR{T}`
  * `RGBA` -> `RGBA{T}`
  * `BGRA` -> `BGRA{T}`
  * `ABGR` -> `ABGR{T}`
  * `GBGR` -> `NTuple{4,T}`
  * `BGRG` -> `NTuple{4,T}`
  * `S` -> 未定義、`R8`に移行

16ビット/コンポーネント:

  * `R` -> `T`
  * `RG` -> `NTuple{2,T}`
  * `RGB` -> `RGB{T}`
  * `RGBA` -> `RGBA{T}`
  * `D` -> 未定義、`R16`に移行

32ビット/コンポーネント:

  * `R` -> `T`
  * `RG` -> `NTuple{2,T}`
  * `RGB` -> `RGB{T}`
  * `RGBA` -> `RGBA{T}`
  * `D` -> 未定義、`R32`に移行

64ビット/コンポーネント:

  * `R` -> `T`
  * `RG` -> `NTuple{2,T}`
  * `RGB` -> `RGB{T}`
  * `RGBA` -> `RGBA{T}`

深度/ステンシル:

  * `D16S8` -> 未定義、`R16`/`R8`に移行
  * `D24S8` -> 未定義、? / `R8`に移行
  * `D32S8` -> 未定義、`R32`/`R8`に移行

圧縮フォーマット: -> 未定義のバイト表現、他のフォーマットに移行

  * `BC`
  * `ETC2`
  * `EAC`
  * `ASTC`
  * `PVRTC`

```julia
format_type(x)
```

は [`packages/Vulkan/qhpzm/src/formats.jl:100`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl) で定義されています。

```julia
format_type(_)
```

は [`packages/Vulkan/qhpzm/src/formats.jl:101`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl) で定義されています。

```julia
format_type(_)
```

は [`packages/Vulkan/qhpzm/src/formats.jl:103`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl) で定義されています。

```julia
format_type(_)
```

は [`packages/Vulkan/qhpzm/src/formats.jl:104`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl) で定義されています。

```julia
format_type(_)
```

は [`packages/Vulkan/qhpzm/src/formats.jl:105`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl) で定義されています。

```julia
format_type(_)
```

は [`packages/Vulkan/qhpzm/src/formats.jl:109`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl) で定義されています。

```julia
format_type(_)
```

は [`packages/Vulkan/qhpzm/src/formats.jl:110`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl) で定義されています。

```julia
format_type(_)
```

は [`packages/Vulkan/qhpzm/src/formats.jl:111`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl) で定義されています。

```julia
format_type(_)
```

は [`packages/Vulkan/qhpzm/src/formats.jl:112`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl) で定義されています。

```julia
format_type(_)
```

は [`packages/Vulkan/qhpzm/src/formats.jl:113`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl) で定義されています。

```julia
format_type(_)
```

は [`packages/Vulkan/qhpzm/src/formats.jl:114`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl) で定義されています。

```julia
format_type(_)
```

は [`packages/Vulkan/qhpzm/src/formats.jl:115`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl) で定義されています。

```julia
format_type(_)
```

は [`packages/Vulkan/qhpzm/src/formats.jl:116`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl) で定義されています。

```julia
format_type(_)
```

は [`packages/Vulkan/qhpzm/src/formats.jl:117`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl) で定義されています。

```julia
format_type(_)
```

は [`packages/Vulkan/qhpzm/src/formats.jl:118`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl) で定義されています。

```julia
format_type(_)
```

は [`packages/Vulkan/qhpzm/src/formats.jl:119`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl) で定義されています。

```julia
format_type(_)
```

は [`packages/Vulkan/qhpzm/src/formats.jl:120`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl) で定義されています。

```julia
format_type(_)
```

は [`packages/Vulkan/qhpzm/src/formats.jl:121`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl) で定義されています。

```julia
format_type(_)
```

は [`packages/Vulkan/qhpzm/src/formats.jl:122`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl) で定義されています。

```julia
format_type(_)
```

は [`packages/Vulkan/qhpzm/src/formats.jl:123`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl) で定義されています。

```julia
format_type(_)
```

は [`packages/Vulkan/qhpzm/src/formats.jl:124`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl) で定義されています。

```julia
format_type(_)
```

は [`packages/Vulkan/qhpzm/src/formats.jl:125`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl) で定義されています。

```julia
format_type(_)
```

は [`packages/Vulkan/qhpzm/src/formats.jl:126`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl) で定義されています。

```julia
format_type(_)
```

は [`packages/Vulkan/qhpzm/src/formats.jl:127`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl) で定義されています。

```julia
format_type(_)
```

は [`packages/Vulkan/qhpzm/src/formats.jl:128`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl) で定義されています。

```julia
format_type(_)
```

は [`packages/Vulkan/qhpzm/src/formats.jl:129`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl) で定義されています。

```julia
format_type(_)
```

は [`packages/Vulkan/qhpzm/src/formats.jl:130`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl) で定義されています。

```julia
format_type(_)
```

は [`packages/Vulkan/qhpzm/src/formats.jl:131`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl) で定義されています。

```julia
format_type(_)
```

は [`packages/Vulkan/qhpzm/src/formats.jl:132`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl) で定義されています。

```julia
format_type(_)
```

は [`packages/Vulkan/qhpzm/src/formats.jl:133`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl) で定義されています。

```julia
format_type(_)
```

は [`packages/Vulkan/qhpzm/src/formats.jl:134`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl) で定義されています。

```julia
format_type(_)
```

は [`packages/Vulkan/qhpzm/src/formats.jl:135`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl) で定義されています。

```julia
format_type(_)
```

は [`packages/Vulkan/qhpzm/src/formats.jl:136`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl) で定義されています。

```julia
format_type(_)
```

は [`packages/Vulkan/qhpzm/src/formats.jl:137`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl) で定義されています。

```julia
format_type(_)
```

は [`packages/Vulkan/qhpzm/src/formats.jl:138`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl) で定義されています。

```julia
format_type(_)
```

は [`packages/Vulkan/qhpzm/src/formats.jl:139`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl) で定義されています。

```julia
format_type(_)
```

は [`packages/Vulkan/qhpzm/src/formats.jl:140`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl) で定義されています。

```julia
format_type(_)
```

は [`packages/Vulkan/qhpzm/src/formats.jl:141`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl) で定義されています。

```julia
format_type(_)
```

は [`packages/Vulkan/qhpzm/src/formats.jl:142`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl) で定義されています。

```julia
format_type(_)
```

は [`packages/Vulkan/qhpzm/src/formats.jl:143`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl) で定義されています。

```julia
format_type(_)
```

は [`packages/Vulkan/qhpzm/src/formats.jl:144`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl) で定義されています。

```julia
format_type(_)
```

は [`packages/Vulkan/qhpzm/src/formats.jl:145`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl) で定義されています。

```julia
format_type(_)
```

は [`packages/Vulkan/qhpzm/src/formats.jl:146`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl) で定義されています。

```julia
format_type(_)
```

は [`packages/Vulkan/qhpzm/src/formats.jl:147`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl) で定義されています。

```julia
format_type(_)
```

は [`packages/Vulkan/qhpzm/src/formats.jl:148`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl) で定義されています。

```julia
format_type(_)
```

は [`packages/Vulkan/qhpzm/src/formats.jl:149`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl) で定義されています。

```julia
format_type(_)
```

は [`packages/Vulkan/qhpzm/src/formats.jl:150`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl) で定義されています。

```julia
format_type(_)
```

は [`packages/Vulkan/qhpzm/src/formats.jl:151`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl) で定義されています。

```julia
format_type(_)
```

は [`packages/Vulkan/qhpzm/src/formats.jl:152`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl) で定義されています。

```julia
format_type(_)
```

は [`packages/Vulkan/qhpzm/src/formats.jl:153`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl) で定義されています。

```julia
format_type(_)
```

は [`packages/Vulkan/qhpzm/src/formats.jl:154`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl) で定義されています。

```julia
format_type(_)
```

は [`packages/Vulkan/qhpzm/src/formats.jl:155`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl) で定義されています。

```julia
format_type(_)
```

は [`packages/Vulkan/qhpzm/src/formats.jl:156`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl) で定義されています。

```julia
format_type(_)
```

は [`packages/Vulkan/qhpzm/src/formats.jl:157`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl) で定義されています。

```julia
format_type(_)
```

は [`packages/Vulkan/qhpzm/src/formats.jl:158`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl) で定義されています。

```julia
format_type(_)
```

は [`packages/Vulkan/qhpzm/src/formats.jl:159`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl) で定義されています。

```julia
format_type(_)
```

は [`packages/Vulkan/qhpzm/src/formats.jl:160`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl) で定義されています。

```julia
format_type(_)
```

は [`packages/Vulkan/qhpzm/src/formats.jl:161`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl) で定義されています。

```julia
format_type(_)
```

は [`packages/Vulkan/qhpzm/src/formats.jl:162`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl) で定義されています。

```julia
format_type(_)
```

は [`packages/Vulkan/qhpzm/src/formats.jl:171`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl) で定義されています。

```julia
format_type(_)
```

は [`packages/Vulkan/qhpzm/src/formats.jl:172`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl) で定義されています。

```julia
format_type(_)
```

は [`packages/Vulkan/qhpzm/src/formats.jl:173`](file:///home/terasaki/.julia/packages/Vulkan/qhpzm/src/formats.jl) で定義されています。
