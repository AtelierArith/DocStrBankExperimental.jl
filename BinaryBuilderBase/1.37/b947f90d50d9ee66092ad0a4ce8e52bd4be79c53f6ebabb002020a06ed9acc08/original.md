```
expand_microarchitectures(p::AbstractPlatform, [microarchitectures::Vector{String}])
```

Given a `Platform`, returns a vector of `Platforms` with differing `march` attributes as specified by the `ARCHITECTURE_FLAGS` mapping.  If the given `Platform` alread has a `march` tag specified, only that platform is returned.  If the `microarchitectures` argument is given, limit the expansion to the given microarchitectures.

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
