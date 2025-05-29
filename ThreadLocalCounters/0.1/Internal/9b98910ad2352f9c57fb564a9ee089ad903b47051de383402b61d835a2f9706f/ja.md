# ThreadLocalCounters

[![Dev](https://img.shields.io/badge/docs-dev-blue.svg)](https://juliaconcurrent.github.io/ThreadLocalCounters.jl/dev) [![CI](https://github.com/JuliaConcurrent/ThreadLocalCounters.jl/actions/workflows/ci.yml/badge.svg)](https://github.com/JuliaConcurrent/ThreadLocalCounters.jl/actions/workflows/ci.yml)

ThreadLocalCounters.jlは、コードの位置にカウンタを関連付けるためのマクロ`@tlc`を提供します。

```jldoctest README
julia> using ThreadLocalCounters

julia> hello_world() = @tlc hello_world;
```

インストールされたカウンタは、`ThreadLocalCounters.list`を使用して列挙できます：

```JULIA
julia> ThreadLocalCounters.list(; all = true)
1-element Vector{ThreadLocalCounters.Internal.ThreadLocalCounter}:
 [0] hello_world @Main #= REPL[2]:2 =#
```

スレッドローカルカウンタは、プログラムが関連付けられたコードの位置に到達するたびにインクリメントされます：

```JULIA
julia> hello_world();

julia> ThreadLocalCounters.list()
1-element Vector{ThreadLocalCounters.Internal.ThreadLocalCounter}:
 [1] hello_world @Main #= REPL[2]:2 =#

julia> hello_world();

julia> ThreadLocalCounters.list()
1-element Vector{ThreadLocalCounters.Internal.ThreadLocalCounter}:
 [2] hello_world @Main #= REPL[2]:2 =#
```
