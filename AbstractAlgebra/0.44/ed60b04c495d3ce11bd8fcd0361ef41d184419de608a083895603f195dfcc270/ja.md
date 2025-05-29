```
Perm{T<:Integer}
```

順列の型。フィールド名:

  * `d::Vector{T}` - 順列を表すベクトル
  * `modified::Bool` - サイクル分解の有効性をチェックするビット
  * `cycles::CycleDec{T}` - （キャッシュされた）サイクル分解

順列 $p$ は、$1$ から $n$ までの $n$ 個の整数のベクトル（`p.d`）で構成されます。ベクトルの $i$ 番目のエントリが $j$ の場合、これは $p$ が $i \to j$ に送ることを意味します。サイクル分解（`p.cycles`）は必要に応じて計算され、直接アクセスするべきではありません。代わりに [`cycles(p)`](@ref) を使用してください。

`Perm` の内部コンストラクタは2つあります:

  * `Perm(n::T)` は長さ $n$ の自明な `Perm{T}`-順列を構築します。
  * `Perm(v::AbstractVector{<:Integer} [,check=true])` は `v` で表される順列を構築します。デフォルトでは `Perm` コンストラクタはベクトルが有効な順列を構成しているかどうかをチェックします。チェックをスキップするには `Perm(v, false)` を呼び出してください。

# 例

```jldoctest
julia> Perm([1,2,3])
()
   
julia> g = Perm(Int32[2,3,1])
(1,2,3)

julia> typeof(g)
Perm{Int32}
```
