```
generate_compiler_wrappers!(platform::AbstractPlatform; bin_path::AbstractString,
                            host_platform::AbstractPlatform = Platform("x86_64", "linux"; libc = "musl", cxxstring_abi = "cxx11"),
                            compilers::Vector{Symbol} = [:c],
                            allow_unsafe_flags::Bool = false,
                            lock_microarchitecture::Bool = true,
                            gcc_version::Union{Nothing,VersionNumber}=nothing,
                            clang_version::Union{Nothing,VersionNumber}=nothing,
                            clang_use_lld::Bool = false,
                            )
```

私たちは、すべてのビルドシステムが私たちのシステム用にビルドするために必要なコンパイラフラグのセットを尊重するように強制するために、ビルド環境内にコンパイララッパースクリプトのセットを生成します。 `platform_envs()`が多くの環境変数を設定する一方で、これらの値はオプション/上書き可能であることに注意してください。 これらの値は、コンパイラバイナリを直接呼び出すことによって上書き可能ですが（例：/opt/{target}/bin/{target}-gcc）、これらのラッパーに埋め込まれたフラグは絶対に必要であり、単純なプログラムでさえそれなしではコンパイルできないため、上書きするのははるかに困難です。
