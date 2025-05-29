```
expand_microarchitectures(ps::Vector{<:Platform}, [microarchitectures::Vector{String}];
                          filter=Returns(true))
```

Expand all platforms in the vector `ps` with the supported microarchitectures.

If the `microarchitectures` argument is given, limit the expansion to the given platforms.  This is useful if you do not want to expand to all available microarchitectures.

The expansion is applied only to the platforms matching the `filter` predicate, by default all platforms.  This is useful if you want to limit the expansion to some platforms, without having to explicitly list its microarchitectures in the second argument.

```jldoctest
julia> using BinaryBuilderBase

julia> expand_microarchitectures(filter!(p -> Sys.islinux(p) && libc(p) == "glibc", supported_platforms()))
15-element Vector{Platform}:
 Linux i686 {libc=glibc, march=pentium4}
 Linux i686 {libc=glibc, march=prescott}
 Linux x86_64 {libc=glibc, march=x86_64}
 Linux x86_64 {libc=glibc, march=avx}
 Linux x86_64 {libc=glibc, march=avx2}
 Linux x86_64 {libc=glibc, march=avx512}
 Linux aarch64 {libc=glibc, march=armv8_0}
 Linux aarch64 {libc=glibc, march=armv8_1}
 Linux aarch64 {libc=glibc, march=armv8_2_crypto}
 Linux aarch64 {libc=glibc, march=a64fx}
 Linux armv6l {call_abi=eabihf, libc=glibc, march=arm1176jzfs}
 Linux armv7l {call_abi=eabihf, libc=glibc, march=armv7l}
 Linux armv7l {call_abi=eabihf, libc=glibc, march=neonvfpv4}
 Linux powerpc64le {libc=glibc, march=power8}
 Linux riscv64 {libc=glibc, march=riscv64}

julia> expand_microarchitectures(filter!(p -> Sys.islinux(p) && libc(p) == "glibc", supported_platforms()), ["x86_64", "avx2"])
8-element Vector{Platform}:
 Linux i686 {libc=glibc}
 Linux x86_64 {libc=glibc, march=x86_64}
 Linux x86_64 {libc=glibc, march=avx2}
 Linux aarch64 {libc=glibc}
 Linux armv6l {call_abi=eabihf, libc=glibc}
 Linux armv7l {call_abi=eabihf, libc=glibc}
 Linux powerpc64le {libc=glibc}
 Linux riscv64 {libc=glibc}

julia> expand_microarchitectures(filter!(p -> Sys.islinux(p) && libc(p) == "glibc", supported_platforms()); filter=p->arch(p)=="x86_64")
10-element Vector{Platform}:
 Linux i686 {libc=glibc}
 Linux x86_64 {libc=glibc, march=x86_64}
 Linux x86_64 {libc=glibc, march=avx}
 Linux x86_64 {libc=glibc, march=avx2}
 Linux x86_64 {libc=glibc, march=avx512}
 Linux aarch64 {libc=glibc}
 Linux armv6l {call_abi=eabihf, libc=glibc}
 Linux armv7l {call_abi=eabihf, libc=glibc}
 Linux powerpc64le {libc=glibc}
 Linux riscv64 {libc=glibc}
```
