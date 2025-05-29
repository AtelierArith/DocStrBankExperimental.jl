```
DenseLinear{T,R} <: AbstractLinear{T,R}

DenseLinear{T,R}(itr; basis::Basis)
```

イテレータ `itr` によって提供された項-係数ペアから、項の型 `T` と係数の型 `R` を持つ `DenseLinear` 型の線形結合を構築します。

このタイプの線形結合は内部的に `Vector`（または、より一般的には `AbstractArray`）として保存されます。必須のキーワード引数 `basis` は、項と `Vector`（または `Array`）のエントリとの間の変換に使用されます。2つの `DenseLinear` 要素を含む操作は、2つの基底が同一である場合（`===` の意味で）に、はるかに高速です。

このコンストラクタの他の使い方については `AbstractLinear` の下で議論されています。

関連情報としては [`Basis`](@ref), [`AbstractLinear`](@ref), [`Linear`](@ref), [`Linear1`](@ref), [`basis`](@ref), [`coordinates`](@ref) を参照してください。

# 例

```jldoctest
julia> azbasis = Basis('a':'z')
Basis('a':1:'z')

julia> a = DenseLinear('x' => 1, 'y' => 2; basis = azbasis)
DenseLinear{Char, Int64} with 2 terms:
'x'+2*'y'

julia> a + 'z'
DenseLinear{Char, Int64} with 3 terms:
'x'+2*'y'+'z'

julia> a + 'X'
ERROR: KeyError: key 'X' not found
[...]

julia> b = DenseLinear('x' => -1, 'z' => 3; basis = azbasis)
DenseLinear{Char, Int64} with 2 terms:
-'x'+3*'z'

julia> a + b
Linear{Char, Int64} with 2 terms:
2*'y'+3*'z'

julia> c = DenseLinear('a' => 5; basis = Basis('a':'c'))
DenseLinear{Char, Int64} with 1 term:
5*'a'

julia> add!(a, c)
DenseLinear{Char, Int64} with 3 terms:
5*'a'+'x'+2*'y'

julia> add!(c, a)
ERROR: KeyError: key 'x' not found
```
