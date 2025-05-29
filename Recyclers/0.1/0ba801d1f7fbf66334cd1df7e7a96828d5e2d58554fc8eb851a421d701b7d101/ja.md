# Recyclers

[![Dev](https://img.shields.io/badge/docs-dev-blue.svg)](https://juliaconcurrent.github.io/Recyclers.jl/dev) [![CI](https://github.com/JuliaConcurrent/Recyclers.jl/actions/workflows/test.yml/badge.svg)](https://github.com/JuliaConcurrent/Recyclers.jl/actions/workflows/test.yml) [![Aqua QA](https://raw.githubusercontent.com/JuliaTesting/Aqua.jl/master/badge.svg)](https://github.com/JuliaTesting/Aqua.jl)

Recyclers.jlは、マルチタスクのJuliaプログラムにおけるメモリ再利用パターンを実装するためのツールセットです。

```jldoctest Recyclers
julia> using Recyclers

julia> recycler = Recyclers.CentralizedRecycler(() -> zeros(3));

julia> xs = Recyclers.get!(recycler)  # キャッシュされたオブジェクトを取得するか、新しいものを作成します
3-element Vector{Float64}:
 0.0
 0.0
 0.0

julia> Recyclers.recycle!(recycler, xs)  # 再利用された場合は`true`を返します
true
```
