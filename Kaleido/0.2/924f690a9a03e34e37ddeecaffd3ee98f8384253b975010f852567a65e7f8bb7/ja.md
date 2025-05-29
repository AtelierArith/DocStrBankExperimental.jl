```
FLens(functor_based_lens) :: Lens
```

`FLens`は、`Lens`を作成するための代替（「同型」）の方法を提供します。これは、リンクリストの最後のアイテムのように動的に決定される「フィールド」にアクセスするのに便利です。

（注：最初に例を見た方が良いかもしれません。）

`FLens`は、`functor_based_lens`（2つの引数を取る呼び出し可能なオブジェクト）を`Setfield`で定義された`Lens`に変換します。呼び出し可能な`functor_based_lens`は、次の2つの引数を受け取ります。

1. `setter`：フィールド内の値を受け取り、`Kaleido.fmap`の2番目の引数に渡すことができるオブジェクトを返す1引数の呼び出し可能なオブジェクト。
2. `obj`：フィールドにアクセスされるオブジェクト。

*非公式に*、上記の関数のシグネチャは次のように書くことができます。

```julia
FLens(functor_based_lens) :: Lens
functor_based_lens(setter, obj)
setter(field::A) :: F{A} where {F <: Functor}
fmap(f, ::F{A}) :: F{B} where {F <: Functor}
f(field::A) :: B
```

（注：実際のコードには`Functor`はありません）

# 例

以下は、`FLens`を使用して`@lens _[1]`を実装したものです。

```jldoctest
julia> using Setfield

julia> using Kaleido: FLens, fmap

julia> fst = FLens((f, obj) -> fmap(x -> (x, obj[2:end]...), f(obj[1])));

julia> get((1, 2, 3), fst)
1

julia> set((1, 2, 3), fst, 100)
(100, 2, 3)
```

典型的な`FLens`の使用法は次の形をしています。

```julia
FLens((f, obj) -> fmap(x -> SET(obj, x), f(GET(obj))))
```

ここで

  * `SET(obj, x)`は、`obj`のフィールドを値`x`に設定します。
  * `GET(obj)`は、フィールドの値を取得します。

`GET`と`SET`が行うことは、`Setfield.get`と`Setfield.set`に似ているように見えるかもしれません。実際、任意のレンズは`FLens`に変換できます。

```jldoctest
julia> using Setfield

julia> using Kaleido: FLens, fmap

julia> asflens(lens::Lens) =
           FLens((f, obj) -> fmap(x -> set(obj, lens, x), f(get(obj, lens))));

julia> dot_a = asflens(@lens _.a);

julia> get((a=1, b=2), dot_a)
1

julia> set((a=1, b=2), dot_a, 100)
(a = 100, b = 2)
```

`FLens`が通常の`Lens`に「同型」であるなら、なぜ`Setfield.get`と`Setfield.set`を直接定義しないのでしょうか？（それらは理解しやすいです。）

これは、`FLens`が関心のある「フィールド」が動的に決定される場合に便利だからです。たとえば、リンクリストの最後のアイテムへのレンズは次のように定義できます。

```jldoctest
julia> using Setfield

julia> using Kaleido: FLens, fmap

julia> struct Cons{T, S}
           car::T
           cdr::S
       end

julia> last_impl(f, list, g) =
           if list.cdr === nothing
               h = x -> g(Cons(x, nothing))
               fmap(h, f(list.car))
           else
               h = x -> g(Cons(list.car, x))
               last_impl(f, list.cdr, h)
           end;

julia> lst = FLens((f, list) -> last_impl(f, list, identity));

julia> list = Cons(1, Cons(2, Cons(3, nothing)));

julia> get(list, lst)
3

julia> set(list, lst, :last) === Cons(1, Cons(2, Cons(:last, nothing)))
true
```

`last_impl`が、`fmap`の最初の引数として渡されるクロージャ`h`を動的に構築することに注意してください。同じレンズを`Setfield.get`と`Setfield.set`を直接定義することで実装することも可能ですが、これらの2つの関数は最後のアイテムに再帰するための重複したコードを持つことになります。

もう一つの（限られた？）利点は、`FLens`が`modify`を使用する際により効率的である可能性があることです。これは、`FLens`が「フィールド」への1回の再帰で`modify`を行うことができるのに対し、`get`と`set`では2回の再帰が必要だからです。これは、特に複雑なオブジェクトとレンズに関連しており、`modify`で使用される`get`と`set`がインライン化できない場合（たとえば、型の不安定性のため）に重要です。

`FLens`は、フィールドにいくつかの制約を課すためにも使用できます。ただし、この目的には[`constraining`](@ref)を使用する方が良いかもしれません。

```jldoctest
julia> using Setfield

julia> using Kaleido: FLens, fmap

julia> fstsnd = FLens((f, obj) -> fmap(
           x -> (x, x, obj[3:end]...),
           begin
               @assert obj[1] == obj[2]
               f(obj[1])
           end,
       ));

julia> get((1, 1, 2), fstsnd)
1

julia> set((1, 1, 2), fstsnd, 100)
(100, 100, 2)
```

# 補足

`FLens`は、[Haskellのレンズ](http://hackage.haskell.org/package/lens)で使用される形式主義を模倣しています。レンズの紹介として、Simon Peyton Jonesによるトーク[レンズ：構成的データアクセスと操作](https://skillsmatter.com/skillscasts/4251-lenses-compositional-data-access-and-manipulation)を強くお勧めします。このトークでは、Haskellでのレンズの簡略化された形式が詳細に説明されています。

```haskell
type Lens' s a = forall f. Functor f
                        => (a -> f a) -> s -> f s
```

非公式に、この型同義語は`FLens`のシグネチャにマッピングされます。

```julia
FLens(((::A -> ::F{A}), ::S) -> ::F{S} where F <: Functor) :: Lens
```
