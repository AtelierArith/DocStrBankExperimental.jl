```
SubDitStr{D,N,T<:Integer} <: Integer
```

この構造体は、`DitStr`の`SubString`のようなオブジェクトです（`SubString`はスライスされた文字列の公式実装であり、参照のために[String](https://docs.julialang.org/en/v1/base/strings/#Base.SubString)を参照してください）。このスライスは、コピーを作成するのではなく、親の`DitStr`へのビューを返します（文字列のための`@views`マクロに似ています）。

`SubDitStr`は、全体のヒルベルト空間の部分空間内の量子ビット構成を記述するために使用できます。`DitStr`と同様の`getindex`、`length`関数を提供します。

```
SubDitStr(dit::DitStr{D,N,T}, i::Int, j::Int)
SubDitStr(dit::DitStr{D,N,T}, r::AbstractUnitRange{<:Integer})
```

または、`DitStr`のための`@views`マクロを使用して（このマクロは`begin`と`end`構文をサポートすることであなたの生活を楽にします）：

```
@views dit[i:j]
```

`SubDitStr`を返します。

### 例

```jldoctest
julia> x = DitStr{3, 5}(71)
02122 ₍₃₎

julia> sx =  SubDitStr(x, 2, 4) 
SubDitStr{3, 5, Int64}(02122 ₍₃₎, 1, 3)

julia> @views x[2:end] 
SubDitStr{3, 5, Int64}(02122 ₍₃₎, 1, 4)

julia> sx == dit"212;3"
true
```
