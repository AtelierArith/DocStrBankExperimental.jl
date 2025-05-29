```
Size(dims::Int...)
```

`Size` は `StaticArrays` API 全体で配列のサイズに関する *コンパイル時* の知識を記述するために広く使用されます。次元は型パラメータとして保存され、コンパイラによって静的に伝播されるため、効率的で型推論可能なコードが生成されます。たとえば、ゼロの静的行列を作成するには、`A = zeros(SMatrix{3,3})` を使用します。`A` の静的サイズは `Size(A)` で取得できます（`size(zeros(3,3))` の代わりに、これは `Base.Tuple{2,Int}` を返します）。

次元が静的に知られていない場合（例えば、標準の `Array` の場合）、[`Dynamic()`](@ref) を `Int` の代わりに使用する必要があります。

```
Size(a::AbstractArray)
Size(::Type{T<:AbstractArray})
```

`Size` コンストラクタは、与えられた配列から静的な次元情報を抽出するために使用できます。例えば：

```julia-repl
julia> Size(zeros(SMatrix{3, 4}))
Size(3, 4)

julia> Size(zeros(3, 4))
Size(StaticArrays.Dynamic(), StaticArrays.Dynamic())
```

これは、静的サイズの配列のサイズに基づく「トレイト」ベースのディスパッチなど、複数の用途があります。例えば：

```julia
det(x::StaticMatrix) = _det(Size(x), x)
_det(::Size{(1,1)}, x::StaticMatrix) = x[1,1]
_det(::Size{(2,2)}, x::StaticMatrix) = x[1,1]*x[2,2] - x[1,2]*x[2,1]
# 必要に応じて他の定義
```
