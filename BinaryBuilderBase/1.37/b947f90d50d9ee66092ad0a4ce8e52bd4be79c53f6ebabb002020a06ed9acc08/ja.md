```
expand_microarchitectures(p::AbstractPlatform, [microarchitectures::Vector{String}])
```

`Platform`を与えると、`ARCHITECTURE_FLAGS`マッピングで指定された異なる`march`属性を持つ`Platforms`のベクターを返します。与えられた`Platform`にすでに`march`タグが指定されている場合、そのプラットフォームのみが返されます。`microarchitectures`引数が指定されている場合、展開を指定されたマイクロアーキテクチャに制限します。

```jldoctest
julia> using BinaryBuilderBase

julia> expand_microarchitectures(Platform("x86_64", "freebsd"))
4-element Vector{Platform}:
 FreeBSD x86_64 {march=x86_64}
 FreeBSD x86_64 {march=avx}
 FreeBSD x86_64 {march=avx2}
 FreeBSD x86_64 {march=avx512}

julia> expand_microarchitectures(Platform("armv7l", "linux"))
2-element Vector{Platform}:
 Linux armv7l {call_abi=eabihf, libc=glibc, march=armv7l}
 Linux armv7l {call_abi=eabihf, libc=glibc, march=neonvfpv4}

julia> expand_microarchitectures(Platform("aarch64", "linux"), ["armv8_0", "a64fx"])
2-element Vector{Platform}:
 Linux aarch64 {libc=glibc, march=armv8_0}
 Linux aarch64 {libc=glibc, march=a64fx}

julia> expand_microarchitectures(Platform("i686", "windows"))
2-element Vector{Platform}:
 Windows i686 {march=pentium4}
 Windows i686 {march=prescott}
```
