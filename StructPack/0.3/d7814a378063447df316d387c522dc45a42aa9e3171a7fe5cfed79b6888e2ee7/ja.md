```
@pack [context] target [in format] [(constructor...)] [{type parameters...}] [[formats...]]
```

指定された `target` の型のパッキング / アンパッキングコードを生成するための便利なマクロです。

## 引数

### target

この引数は `T`、`{<: T}`、または `{S <: T}` の形式でなければなりません。ここで `T` は既存の型で、`S` はコンストラクタ内で再利用できる変数名です（下記参照）。これは [`@pack`](@ref) の唯一の必須引数です。

### context

この（オプションの）引数は既存のサブタイプ `C <: Context` でなければなりません。生成されるコードはこのコンテキストに制限されます。`C` のインスタンスを渡すことはできず、実際の型が必要です。

### format

この（オプションの）パターンは、関数 [`format`](@ref) を特化させることによって、型ターゲットのデフォルトフォーマットを設定するために使用できます。たとえば、`@pack T in F` で `F <: Format` の場合、`StructPack.format(::Type{T}) = F()` が定義されます。

特別な構文 `F[C]` は、`F <: Format` かつ `C <: Context` の場合に `ContextFormat{C, F}` のショートカットとして利用可能です。これは、下記の `(formats...)` を介してフィールドおよび型パラメータフォーマットを指定する際に主に便利です。

### constructor

この（オプションの）引数は、型 `T` の値がフォーマット `F <: AbstractStructFormat` でパック / アンパックされるときに、関数 [`destruct`](@ref)、[`construct`](@ref)、[`fieldnames`](@ref)、および（オプションで）[`fieldtypes`](@ref) に影響を与えます。

  * `(a, b, ...; c, d, ...)` のような（キーワード）引数のリストである場合、コンストラクタ `T` は [`construct`](@ref) でそれぞれの引数を使って呼び出されます。
  * `f(a, b, ...; c, d, ...)` のような関数呼び出し式である場合、関数 `f` は [`construct`](@ref) でそれぞれの引数を使って呼び出されます。

いずれの場合も、`[:a, :b, ..., :c, :d, ...]` のフィールドのみが [`fieldnames`](@ref) によってこの順序で返されます。これは、[`destruct`](@ref) を介してどのフィールドがパックされるかにも影響します。

型仕様が存在する場合（例：`(a::Int, b; c::Float64)`）、[`fieldtypes`](@ref) によって返されるそれぞれのフィールド型は上書きされます。

### type parameters

この（オプションの）引数は関数 [`typeparamtypes`](@ref) に影響を与えます。`{A::Ta, B::Tb, ...}` の形式の式を期待しており、ラベル `A, B, ...` はオプションで、`Ta, Tb, ...` はそれぞれの型パラメータの型を示します。

`T` が [`TypeFormat`](@ref) でパック / アンパックされる場合や、値 `val::T` が [`TypedFormat`](@ref) でパック / アンパックされる場合には、型パラメータ型の指定が必要です。

簡単な例として、`@pack {<: Array} {::Type, ::Int}` を考えてみましょう。これは基本的な配列型のパック / アンパックを可能にします：

```
@pack {<: Array} {::Type, ::Int}
bytes = pack(Array{Float64, 3})
unpack(bytes, Type) # 成功裏に Array{Float64, 3} を返します
```

### formats

この（オプションの）引数は関数 [`fieldformats`](@ref) および [`typeparamformats`](@ref) に影響を与えます。これは、フォーマット仕様のリスト `[a in Fa, b in Fb, C in FC, ...]` であることが期待されます。ここで、ラベル `a, b, C, ...` は `T` のフィールド名または `{type parameters...}` 引数で確立された型パラメータ名を指し、`Fa, Fb, FC, ...` は既存の `Format` のサブタイプです（上記の `in format` を参照）。

便利のために、構文 `[(a, b, ...) in F]` は `[a in F, b in F, ...]` に変換されます。

## 例

```julia
using StructPack

struct A
  a :: Int
  b :: Vector{Float64}
  c :: Vector{Float64}
end

A(a, b) = A(a, b, rand(5))

@pack A in StructFormat (a, b) [b in BinVectorFormat]

A(a, b; c) = A(a, b, c)

@pack A in StructFormat (a, b; c) [(b, c) in BinVectorFormat]

myA(a) = A(a, [], [])

@pack A in StructFormat myA(a)
```
