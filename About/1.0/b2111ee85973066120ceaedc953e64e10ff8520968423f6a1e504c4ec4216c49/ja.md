```
About
```

時には、関数、型、値、またはまったく別のものについて、作業している内容をもっと知りたいと思うことがあります。

このパッケージは、その質問に答えるのを助けるユーティリティであり、任意のJuliaオブジェクトに適用できる単一の関数`about`をエクスポートします。

# 拡張ヘルプ

## 例

**モジュールに適用**

```julia-repl
julia> about(About)
Module About [69d22d85-9f48-4c46-bbbe-7ad8341ff72a]
  Version 0.1.0 loaded from ~/.julia/dev/About

Directly depends on 4 packages (+9 indirectly):
• PrecompileTools (+5)  • InteractiveUtils (+3)  • StyledStrings  • JuliaSyntaxHighlighting (+1)

Exports 2 names:
• About  • about
```

**シングルトン値に適用**

```julia-repl
julia> about(ℯ)
Irrational{:ℯ} (<: AbstractIrrational <: Real <: Number <: Any), occupies 0B.
singleton
```

**浮動小数点数に適用**

```julia-repl
julia> about(Float64(ℯ))
Float64 (<: AbstractFloat <: Real <: Number <: Any), occupies 8B.

 0100000000000101101111110000101010001011000101000101011101101001
 ╨└────┬────┘└────────────────────────┬─────────────────────────┘
 +    2^1   ×                1.359140914229522545
 = 2.7182818284590451
```

**文字に適用**

```julia-repl
julia> about('√')
Char (<: AbstractChar <: Any), occupies 4B.

     ┌2─┐   ┌2─┐┌──1──┐┌A─┐
 11100010 10001000 10011010 00000000
 └─0xe2─┘ └─0x88─┘ └─0x9a─┘ └─0x00─┘
 = U+221A

 Unicode '√', category: Symbol, math (Sm)
```

**構造体型に適用**

```julia-repl
julia> about(Dict{Symbol, Int})
Concrete DataType defined in Base, 64B
  Dict{Symbol, Int64} <: AbstractDict{Symbol, Int64} <: Any

Struct with 8 fields:
• slots    *Memory{UInt8}
• keys     *Memory{Symbol}
• vals     *Memory{Int64}
• ndel      Int64
• count     Int64
• age       UInt64
• idxfloor  Int64
• maxprobe  Int64

 ■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■
    *       *       *       8B      8B      8B      8B      8B

 * = Pointer (8B)
```

**関数に適用**

```julia-repl
julia> about(sum, Set{Int})
sum (generic function with 10 methods)
 Defined in Base(8) extended in Base.MPFR(1) and Base.GMP(1).

 Matched 1 method :: Int64
  sum(a; kw...) @ Base reduce.jl:561

 Method effects
  ✗ consistent     might not return or terminate consistently
  ✔ effect free    guaranteed to be free from externally semantically visible side effects
  ✗ no throw       may throw an exception
  ✗ terminates     might not always terminate
  ✔ no task state  guaranteed not to access task state (allowing migration between tasks)
  ~ inaccessible memory only  may access or modify mutable memory iff pointed to by its call arguments
  ✗ no undefined behaviour  may execute undefined behaviour
  ✔ non-overlayed  may call methods from an overlayed method table
```

## フェイス

これらは`About`が定義するフェイスであり、出力のスタイルを変更するためにカスタマイズできます。

  * `about_module` (明るい赤)
  * `about_pointer` (シアン)
  * `about_count` (太字)
  * `about_bytes` (太字)
  * `about_cycle1` (明るい青)
  * `about_cycle2` (明るい緑)
  * `about_cycle3` (明るい黄)
  * `about_cycle4` (明るいマゼンタ)

## 公開API

  * `about`
  * `memorylayout` (拡張可能)
  * `elaboration` (拡張可能)
