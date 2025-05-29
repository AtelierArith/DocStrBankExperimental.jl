```
expand_microarchitectures(ps::Vector{<:Platform}, [microarchitectures::Vector{String}];
                          filter=Returns(true))
```

ベクター `ps` 内のすべてのプラットフォームをサポートされているマイクロアーキテクチャで拡張します。

`microarchitectures` 引数が指定されている場合、拡張を指定されたプラットフォームに制限します。これは、すべての利用可能なマイクロアーキテクチャに拡張したくない場合に便利です。

拡張は、デフォルトですべてのプラットフォームに対して、`filter` プレディケートに一致するプラットフォームのみに適用されます。これは、2 番目の引数にマイクロアーキテクチャを明示的にリストすることなく、いくつかのプラットフォームに拡張を制限したい場合に便利です。

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
