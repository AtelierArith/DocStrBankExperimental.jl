@symbolic_model は、シンボルによって生成された理論の自由モデルを生成します。

これは、Catlab の @syntax マクロとの後方互換性があります。

これを考える一つの方法は、すべての型コンストラクタに対して、任意の Julia 値からその型の「シンボリック」要素を構築する追加の項コンストラクタを追加することです。この項コンストラクタは「generator」と呼ばれます。

`@symbolic_model` の呼び出しは、以下のものを生成します。

1. 各型コンストラクタのための構造体を持つモジュールで、単一の型パラメータ `T` と二つのフィールド `args` と `type_args` を持ちます。この構造体のインスタンスは、型コンストラクタが `type_args` に適用されたことによって与えられる型の要素と考えられます。型パラメータは、要素を生成するために使用された項コンストラクタを指し、特別な項コンストラクタ `:generator` も含まれ、その単一の引数は `Any` です。

例えば、カテゴリの理論では、次のような要素があるかもしれません。

```
using .FreeCategory
x = Ob{:generator}([:x], [])
y = Ob{:generator}([:y], [])
f = Hom{:generator}([:f], [x, y])
g = Hom{:generator}([:g], [y, x])
h = Hom{:compose}([f, g], [x, x])
```

2. モジュール内のすべての項コンストラクタとフィールドアクセサ（すなわち `compose, id, dom, codom` などのもの）に対するメソッド（エクスポートされていない）があり、項を構築します。
3. この生成されたモデルの型を使用した理論のデフォルトインスタンス（すなわち、モデルパラメータなし）があり、このインスタンス内のメソッドは、正規化のために書き換えを行うために `@symbolic_model` の本体によってオーバーライドされることがあります。例えば、結合的および単位的操作をフラット化することです。
4. ジェネレーターを導入することを可能にする型コンストラクタの強制メソッド。

```
x = ThCategory.Ob(FreeCategory.Ob, :x)
y = ThCategory.Ob(FreeCategory.Ob, :y)
f = ThCategory.Hom(:f, x, y)
```

インスタンスとこれらの強制メソッドの両方において、他の引数から推論できない場合、期待される型を最初の引数として与えなければならないことに注意してください。例えば、次のようにする代わりに

```
munit() = ...
```

次のようにします。

```
munit(::Type{FreeSMC.Ob}) = ...
```

同様に、次のようにする代わりに

```
ThCategory.Ob(x::Any) = ...
```

次のようにします。

```
ThCategory.Ob(::Type{FreeCategory.Ob}, x::Any) = ...
```

例:

```julia
@symbolic_model FreeCategory{ObExr, HomExpr} ThCategory begin
  compose(f::Hom, g::Hom) = associate_unit(new(f,g; strict=true), id)
end
```

これにより、次のようなものが生成されます。

```julia
module FreeCategory
export Ob, Hom
using ..__module__

module Meta
  const theory_module = ThCategory
  const theory = ThCategory.Meta.theory
  const theory_type = ThCategory.Meta.T
end

struct Ob{T} <: __module__.ObExpr{T} # T is :generator or a Symbol
  args::Vector
  type_args::Vector{GATExpr}
end

struct Hom{T} <: __module__.HomExpr{T}
  args::Vector
  type_args::Vector{GATExpr}
end

dom(x::Hom) = x.type_args[1]

codom(x::Hom) = x.type_args[2]

function compose(f::Hom, g::Hom; strict=true)
  if strict && !(codom(f) == dom(g))
    throw(SyntaxDomainError(:compose, [f, g]))
  end
  Hom{:compose}([f, g], [dom(f), codom(g)])
end

function id(x::Ob)
  Ob{:id}([x], [x, x])
end
end

# デフォルトの実装 

function ThCategory.dom(x::FreeCategory.Hom)::FreeCategory.Ob
  FreeCategory.dom(x)
end

function ThCategory.Ob(::Type{FreeCategory.Ob}, __value__::Any)::FreeCategory.Ob
  FreeCategory.Ob{:generator}([__value__], [])
end

function ThCategory.id(A::FreeCategory.Ob)::FreeCategory.Hom
  FreeCategory.id(A)
end

function ThCategory.compose(f::FreeCategory.Hom, g::FreeCategory.Hom; strict=true)
  associate_unit(FreeCategory.compose(f, g; strict), id)
end
```
