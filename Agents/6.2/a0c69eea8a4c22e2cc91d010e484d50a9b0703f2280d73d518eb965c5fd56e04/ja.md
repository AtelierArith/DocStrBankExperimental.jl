```
@agent struct YourAgentType{X}(AgentTypeToInherit) [<: OptionalSupertype]
    extra_property::X
    other_extra_property_with_default::Bool = true
    const other_extra_const_property::Int
    # etc...
end
```

エージェント構造体を定義し、`AgentTypeToInherit`が持つすべてのフィールドと、ユーザーが提供する追加のフィールドを含めます。このマクロは、`const`フィールド宣言や一部のフィールドのデフォルト値など、標準のJulia `mutable struct`コマンドが許可するすべての構文をサポートしています。さらに、結果として得られる型には常にキーワードコンストラクタが定義されます（`@kwdef`を使用）。 

`@agent`を使用することは、Agents.jlのエージェントタイプを作成するための推奨方法です。

`@agent`で作成された構造体はデフォルトで`AbstractAgent`のサブタイプです。すべての`@agent`から作成された構造体は具体的な型であり、`AgentTypeToInherit`自体も具体的であるため、互いにサブタイプにはなれません（具体的な型のみがフィールドを持ちます）。`YourAgentType`が`AbstractAgent`以外の何かのサブタイプであることを望む場合は、オプションの引数`OptionalSupertype`を使用してください（それ自体も`AbstractAgent`のサブタイプである必要があります）。

## 使用法

マクロ`@agent`には主に2つの用途があります：

1. エージェント構造体の特定の空間に必要なフィールドを含めること。この場合、最小限のエージェントタイプの1つを`AnotherAgentType`として使用します。
2. すでに存在する別の構造体からフィールドを含める便利な方法であり、これによりJuliaにおける「型継承」のツールキットを確立します。

既存の最小限のエージェントタイプは次のとおりです：

  * [`NoSpaceAgent`](@ref)
  * [`GraphAgent`](@ref)
  * [`GridAgent`](@ref)
  * [`ContinuousAgent`](@ref)
  * [`OSMAgent`](@ref)

これらは、新しい型にどのフィールドを追加するかを説明します。

## 例

### オプションの階層なしの例

次のように使用します。

```julia
@agent struct Person{T}(GridAgent{2})
    age::Int
    moneyz::T
end
```

これは、2次元の[`GridSpace`](@ref)で使用するのに適したエージェントを作成します。

```julia
mutable struct Person{T} <: AbstractAgent
    id::Int
    pos::NTuple{2, Int}
    age::Int
    moneyz::T
end
```

いくつかのフィールドにデフォルト値を使用することもできることに注意してください。この場合、デフォルトでない値を持つフィールド名を指定する必要があります。

```julia
@agent struct Person2{T}(GridAgent{2})
    age::Int = 30
    moneyz::T
end
# デフォルトの年齢値
Person2(id = 1, pos = (1, 1), moneyz = 2000)
# 新しい年齢値
Person2(1, (1, 1), 40, 2000)
```

### オプションの階層を持つ例

上記の構造体を作成し、ユーザー固有のサブタイピング階層を確立する別の方法は次のとおりです。

```julia
abstract type AbstractHuman <: AbstractAgent end

@agent struct Worker(GridAgent{2}) <: AbstractHuman
    age::Int
    moneyz::Float64
end

@agent struct Fisher(Worker) <: AbstractHuman
    fish_per_day::Float64
end
```

これにより、`Fisher`と`Worker`の両方が`AbstractHuman`のサブタイプになります。

```julia
julia> supertypes(Fisher)
(Fisher, AbstractHuman, AbstractAgent, Any)

julia> supertypes(Worker)
(Worker, AbstractHuman, AbstractAgent, Any)
```

`Fisher`は`Worker`のサブタイプではないことに注意してください。`Fisher`は`Worker`からフィールドを継承していますが。

### パラメトリック型の問題を強調する例

Juliaでは、パラメトリック型はユニオン型であることに注意してください。したがって、次のようには使用できません。

```julia
@agent struct Dummy{T}(GridAgent{2})
    moneyz::T
end

@agent struct Fisherino{T}(Dummy{T})
    fish_per_day::T
end
```

`Fisherino`の定義でエラーが発生します。なぜなら、`Dummy{T}`のフィールドを取得できないからです。これはユニオン型だからです。`Dummy`を使用する場合も同様です。`Dummy{Float64}`のみを使用できます。

### 共通のディスパッチとサブタイピングなしの例

複数のディスパッチを利用したい場合、サブタイピング関係を作成する必要がないかもしれません。次の例を考えてみてください。

```julia
@agent struct CommonTraits(GridAgent{2})
    age::Int
    speed::Int
    energy::Int
end
```

そして、これらの特性からさらに2つの構造体が作成されます。

```julia
@agent struct Bird(CommonTraits)
    height::Float64
end

@agent struct Rabbit(CommonTraits)
    underground::Bool
end
```

`Rabbit`と`Bird`の両方にディスパッチする関数を作成したい場合、次のように定義するだけです。

```julia
Animal = Union{Bird, Rabbit}
f(x::Animal) = ... # `CommonTraits`フィールドを使用
```

ただし、`f`内で`x::Animal`を明示的に型注釈する理由は特にありません。型を注釈することは、`Animal`や`Person`のように少なくとも2つの「抽象」グループがある場合にのみ有用です。その場合、次のように定義することが意味を持ちます。

```julia
Person = Union{Fisher, Baker}
f(x::Animal) = ... # `CommonTraits`フィールドを使用
f(x::Person) = ... # すべての「人」が持つフィールドを使用
```

Agents.jlには、エージェントを自動的に作成してモデルに追加する便利な関数[`add_agent!`](@ref)があります。自分でエージェントを作成したい場合は、モデルを最初の引数として受け取るコンストラクタを使用して、`id`などの内部フィールドが自動的に設定されるようにできます。

```julia
model = StandardABM(GridAgent{2}, GridSpace((10,10)))
a = GridAgent{2}(model, (3,4)) # idは自動的に設定されます
```
