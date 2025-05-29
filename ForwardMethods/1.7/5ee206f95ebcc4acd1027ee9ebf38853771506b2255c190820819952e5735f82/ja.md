```
@forward_methods T [field=_field] [map=_map] methods...
```

`x::T`のメソッド定義を、`_field`の値に応じて転送します。

`_field`は次のいずれかの式でなければなりません。

  * `k::Symbol`または`k::QuoteNode`、または`getfield(_, k)`の形の式。この場合、メソッドは`getfield(x, k)`に転送されます。
  * `a.b.c. ...`の形の式。この場合、メソッドは`getfield(getfield(getfield(x, :a), :b), :c) ...`に転送されます。
  * `getproperty(_, k)`の形の式。この場合、メソッドは`getproperty(x, k)`に転送されます。
  * `t[args...]`の形の式。この場合、メソッドは`x[args...]`に転送されます。
  * または、単一引数関数`f`のための`f(_)`の形の式。この場合、メソッドは`f(x)`に転送されます。

以下の記法の目的のために、転送された値を`forwarded_value(x)`と呼びます。

各`method`は次のいずれかの式でなければなりません。

  * `f::Symbol`または`A.f`の形の式。これにより、単一引数関数`f(x)`または`A.f(x)`が`f(forwarded_value(x))`または`A.f(forwarded_value(x))`に転送されます。
  * `f(args...)`または`f(args...; kwargs...)`の形の関数シグネチャ。この形では、`args`の中に`x::T`または`_`（アンダースコア）の形の式が正確に1つ存在しなければなりません。これが位置`i`にある場合、このマクロはこのメソッドを次の定義に転送します。

    `f(args[1], args[2], ..., args[i-1], forwarded_value(x), args[i+1], ..., args[end]; kwargs...)`

    `field`がフィールド`k`の`getfield`を呼び出すことにマッピングされる場合、`::T`または`x::T`の形の引数式を書くこともできます。この場合、このマクロ定義は次のように定義します。

    `f(args[1], ..., args[i-1], ::Type{T}, args[i+1], ..., args[end]; kwargs) = f(args[1], ..., args[i-1], fieldtype(T, k), args[i+1], ..., args[end]; kwargs)`

    これは、例えば、トレイトベースのメソッドを対応するコンテナ型に転送するのに便利です。

各`method`はまた、上記の条件を満たす各サブ式が含まれる`:block`式であることもできます。

## オプション引数

オプションの`map=_map`パラメータを使用すると、結果として転送された式に対して式変換を適用できます。`_map`は、少なくとも1つのアンダースコア`_`プレースホルダーとオプションで`_obj`プレースホルダーを含む式でなければなりません。`_`と`_obj`は、それぞれ変換された関数と初期オブジェクト引数に置き換えられます。

例えば、次のような場合を考えます。

```julia
    struct LockableDict{K,V}
        d::Dict{K,V}
        lock::ReentrantLock
    end
    @forward LockableDict{K,V} field=lock Base.lock Base.unlock
    @forward LockableDict{K,V} field=d map=(begin lock(_obj); try _ finally unlock(_obj) end end) Base.getindex(_, k) 
```

この場合、2番目の文で生成される式は（大まかに）次の形になります。

```julia
    function Base.getindex(l::LockableDict{K,V}, k)
        lock(l)
        try 
            Base.getindex(getfield(l, :d))
        finally
            unlock(l)
        end
    end
```

# 注意事項

  * パラメトリック式は`T`に対して、また`method`の関数シグネチャ形式に対してサポートされています。

# 例

```julia-repl
julia> struct B{T} 
         v::Vector{T}
       end

julia> @forward_methods B{T} field=v Base.firstindex Base.lastindex Base.getindex(_, k::Int) Base.setindex!(x::B, v, k) (Base.eachindex(x::B{T}) where {T})

julia> b = B([1,2,3])
B{Int64}([1, 2, 3])

julia> for i in eachindex(b)
         b[i] = b[i]^2
       end
julia> b[end]
9

julia> struct C
         d::Dict{String,Int}
       end
julia> @forward_methods C field=d Base.keytype(::Type{C}) Base.valtype(::Type{C})

julia> keytype(C)
String 

julia> valtype(C)
Int
```
