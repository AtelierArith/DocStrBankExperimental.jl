# Atomix

[![Dev](https://img.shields.io/badge/docs-dev-blue.svg)](https://juliaconcurrent.github.io/Atomix.jl/dev/) [![CI](https://github.com/JuliaConcurrent/Atomix.jl/actions/workflows/ci.yml/badge.svg)](https://github.com/JuliaConcurrent/Atomix.jl/actions/workflows/ci.yml)

Atomix.jlは、`Base`のマクロのスーパーセットである`@atomic`、`@atomicswap`、および`@atomicreplace`を実装しています。 `Base`で実装されているフィールドに対する原子操作に加えて、配列要素に対する原子操作もサポートしています。

```jldoctest README
julia> using Atomix: @atomic, @atomicswap, @atomicreplace

julia> A = ones(Int, 3);

julia> @atomic A[1] += 1;  # fetch-and-increment

julia> @atomic A[1]
2

julia> @atomicreplace A[begin+1] 1 => 42  # compare-and-swap
(old = 1, success = true)

julia> @inbounds @atomic :monotonic A[begin+1]  # specify ordering and skip bound check
42

julia> @atomicswap A[end] = 123
1

julia> A[end]
123
```
