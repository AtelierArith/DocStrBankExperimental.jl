```
@&(T)
@&(:mut, T)
```

借用型のための型エイリアスマクロ。`@& T`は`Union{T, Borrowed{T}}`に展開され、`@&(:mut, T)`は`Union{T, BorrowedMut{T}}`に展開されます（およびそれらの`LazyAccessor`バージョンも）。

これは、生の値または借用された値のいずれかを受け入れる汎用的なシグネチャを書くのに便利です。

# 例

ここでは、`Vector{Int}`の可変借用を受け入れる関数を定義します。また、ベクターを保護するために[`Mutex`](@ref BorrowChecker.MutexModule.Mutex)の使用を示します。

```julia
julia> function foo(x::@&(:mut, Vector{Int}))
           push!(x, 4)
           return nothing
       end
foo (generic function with 1 method)

julia> m = Mutex([1, 2, 3])
Mutex{Vector{Int64}}([1, 2, 3])

julia> lock(m) do
           @ref_into :mut r = m[]
           foo(r)
       end

julia> println(m)
Mutex{Vector{Int64}}([1, 2, 3, 4])
```
