# PreludeDicts: 辞書とセットのための基本API

[![Dev](https://img.shields.io/badge/docs-dev-blue.svg)](https://juliapreludes.github.io/PreludeDicts.jl/dev) [![CI](https://github.com/JuliaPreludes/PreludeDicts.jl/actions/workflows/ci.yml/badge.svg)](https://github.com/JuliaPreludes/PreludeDicts.jl/actions/workflows/ci.yml) [![Aqua QA](https://raw.githubusercontent.com/JuliaTesting/Aqua.jl/master/badge.svg)](https://github.com/JuliaTesting/Aqua.jl)

PreludeDicts.jlの主な機能は`modify!`であり、非常に柔軟なAPIです（例えば、すべての`Base` APIは`modify!`に基づいて効率的に実装できます）し、拡張可能でもあります（例えば、[ロックフリー辞書](https://github.com/JuliaConcurrent/ConcurrentCollections.jl)はこのAPIをサポートできます）。

PreludeDicts.jlには、効率的でデバッグ可能なエラーハンドリングAPIである[Try.jl](https://github.com/JuliaPreludes/Try.jl)を使用した`tryset!`、`trysetwith!`、`tryget`、`tryinsert!`の関数もあります。

APIリファレンスについては[Documentation](https://juliapreludes.github.io/PreludeDicts.jl/dev/)を参照してください。

## チュートリアル

### `modify!`

`modify!(f, dict, key)`は、キーに関連付けられた値にアクセスし操作するための非常に強力なAPIを提供します。これは、次のような単一引数関数`f`を受け取ります。

  * `key`が存在しない場合は`nothing`
  * `key`に値がある場合はキー-値ペア

引数として受け取り、次のように返すことができます。

  * 値を削除するために`nothing`
  * `value`を挿入するために`Some(value)`

関数`f`は、最適化として次のように返すこともできます。

  * 値を削除するために`Delete(data)`、ただし`data`を呼び出し元に伝播させる
  * 値を変更せずに`Keep(data)`を返し、`data`を呼び出し元に伝播させる

例えば、`modify!`は値を挿入または設定するために使用できます。

```jldoctest PreludeDicts
julia> using PreludeDicts

julia> dict = Dict(:a => 0);

julia> modify!(Returns(Some(111)), dict, :a)
Some(111)

julia> dict[:a]
111
```

または値を削除することもできます。

```jldoctest PreludeDicts
julia> dict = Dict(:a => 0);

julia> modify!(Returns(nothing), dict, :a)

julia> haskey(dict, :a)
false
```

または値にアクセスすることもできます。

```jldoctest PreludeDicts
julia> dict = Dict(:a => 111);

julia> getvalue(x) = x === nothing ? nothing : Some(last(x));

julia> modify!(getvalue, dict, :a)
Some(111)

julia> modify!(getvalue, dict, :b) === nothing
true
```

`modify!`は、上記の操作が関数`f`を使用して動的に制御できるため、強力です。

```jldoctest PreludeDicts
julia> inc!(dict, key) = modify!(dict, key) do slot
           if slot === nothing
               Some(1)
           else
               Some(last(slot) + 1)
           end
       end;

julia> dict = Dict(:a => 111);

julia> inc!(dict, :a)
Some(112)

julia> inc!(dict, :b)
Some(1)

julia> dict == Dict(:a => 112, :b => 1)
true
```

`modify!`が直接実装されている場合（これは一部のJuliaバージョンの`Dict`に当てはまります）、例えば`dict[key] = get(dict, key, 0) + 1`よりも効率的です。これは2回のハッシュ関数呼び出しとプロービングを必要とします。

#### `Keep`と`Delete`

上記の`modify!(getvalue, dict, :a)`は、既存の値を再挿入するため、最大限効率的ではないことに注意してください。マイクロ最適化として、代わりに`Keep`を使用できます。

```jldoctest PreludeDicts
julia> dict = Dict(:a => 111);

julia> getvalue2(x) = x === nothing ? nothing : Keep(last(x));

julia> y = modify!(getvalue2, dict, :a)
Keep(111)

julia> y[]  # ラップされたデータを取得
111

julia> modify!(getvalue2, dict, :b) === nothing
true
```

`pop!`のような関数を効率的に実装するのを助けるために、`modify`は`Delete`もサポートしており、これは`nothing`のように削除を示しますが、データペイロードを持つことができます。

```jldoctest PreludeDicts
julia> y = modify!(Delete, dict, :a)
Delete(:a => 111)

julia> y[]  # ラップされたデータを取得
:a => 111

julia> haskey(dict, :a)
false
```

### `trysetwith!`

`trysetwith!(f, dict, key)`は`get!(f, dict, key)`のようなもので、返される値は`f`によって返された値が挿入されたかどうかをエンコードします。

```jldoctest PreludeDicts
julia> dict = Dict(:a => 111);

julia> trysetwith!(Returns(222), dict, :a)
Try.Err: :a => 111

julia> trysetwith!(Returns(222), dict, :b)
Try.Ok: :b => 222

julia> dict == Dict(:a => 111, :b => 222)
true
```

### `tryset!`

`tryset!(dict, key, value)`は`get!(dict, key, value)`のようなもので、返される値は`value`が挿入されたかどうかをエンコードします。

```jldoctest PreludeDicts
julia> dict = Dict(:a => 111);

julia> tryset!(dict, :a, 222)
Try.Err: :a => 111

julia> tryset!(dict, :b, 222)
Try.Ok: :b => 222

julia> dict == Dict(:a => 111, :b => 222)
true
```

### `tryget`

`tryget(dict, key)`は`dict[key]`に似ていますが、返される値は`key`が存在するかどうかをエンコードします。例外をスローする代わりに。

```jldoctest PreludeDicts
julia> dict = Dict(:a => 111);

julia> tryget(dict, :a)
Try.Ok: 111

julia> tryget(dict, :b)
Try.Err: TypedKeyError: key :b not found
```

### `tryinsert!`

`tryinsert!(set, x)`は`push!(set, x)`のようなもので、返される値はアイテム`x`が挿入されたかどうかをエンコードします。

```jldoctest PreludeDicts
julia> set = Set([111]);

julia> tryinsert!(set, 111)
Try.Err: 111

julia> tryinsert!(set, 222)
Try.Ok: 222

julia> set == Set([111, 222])
true
```

## 議論

### ベンチマーク

`modify!`に基づく実装は、いくつかのベンチマークで40%から50%のパフォーマンス向上を示しています。

```JULIA
julia> using PreludeDictsBenchmarks

julia> suite = PreludeDictsBenchmarks.setup();

julia> results = run(suite)
2-element BenchmarkTools.BenchmarkGroup:
  tags: []
  "TrySet" => 2-element BenchmarkTools.BenchmarkGroup:
          tags: []
          "impl=:tryset!" => Trial(27.639 μs)
          "impl=:tryset_generic!" => Trial(39.650 μs)
  "Increments" => 2-element BenchmarkTools.BenchmarkGroup:
          tags: []
          "impl=:modify!" => Trial(1.001 ms)
          "impl=:modify_generic!" => Trial(1.587 ms)
```

ここで、`_generic!`サフィックスのある実装は、辞書の内部に触れる`modify!`の直接実装に基づいていない一般的な実装を使用しています。

ベンチマークコードについては[`benchmark/PreludeDictsBenchmarks`](benchmark/PreludeDictsBenchmarks)を参照してください。

### `modify!`を使用した`AbstractDict` APIの導出

さまざまな効率的な`AbstractDict` API実装は`modify!`から導出でき、これは強力なAPIの基盤であることを示しています。

```jldoctest PreludeDicts
julia> function getindex′(dict, key)
           y = modify!(Keep, dict, key)
           y === nothing && throw(KeyError(key))
           return last(y[])
       end;

julia> getindex′(Dict(:a => 111), :a)
111

julia> setindex′!(dict, value, key) = modify!(Returns(Some(value)), dict, key);

julia> dict = Dict();

julia> setindex′!(dict, 111, :a);

julia> dict[:a]
111

julia> function pop′!(dict, key)
           pair = modify!(Delete, dict, key)[]
           pair === nothing && throw(KeyError(key))
           return last(pair)
       end;

julia> pop′!(dict, :a)
111

julia> dict == Dict()
true

julia> function get′!(f, dict, key)
           y = modify!(dict, key) do pair
               if pair === nothing
                   Some(f())
               else
                   Keep(last(pair))
               end
           end
           return y isa Keep ? y[] : something(y)
       end;

julia> get′!(() -> 222, dict, :a)
222

julia> dict[:a]
222

julia> get′!(() -> 333, dict, :a)
222

julia> dict[:a]
222
```

### トークンベースのAPIとの比較

他の辞書インターフェースも探求されています。[Dictionaries.jl](https://github.com/andyferris/Dictionaries.jl)は、ハッシュ関数とプロービングを繰り返し呼び出さないようにするためのトークンベースのAPIを持っています。他の言語にも同様のメカニズムがあります。例えば、Rustの`HashMap`には、同じ効果を達成する[`Entry` API](https://doc.rust-lang.org/std/collections/hash_map/enum.Entry.html)があります。しかし、Juliaにはコルーチン（`Task`）があるため、トークンシステムは`modify!`に「同型」であり、一方が他方に基づいて実装できるという点で同じです（以下を参照）。

より重要なことは、`modify!`が*辞書の実装者*に対して、ユーザーによって渡される関数`f`がどのように呼び出されるかについて、より自由を与えることです。例えば、ロックフリー辞書では、複数のタスクが同じスロットを同時に更新しようとする場合、`f`が複数回呼び出される可能性があります。実際、[ConcurrentCollections](https://github.com/JuliaConcurrent/ConcurrentCollections.jl)は、`ConcurrentDict`を操作するために同様のAPIを使用しています。（TODO: ConcurrentCollections.jlでPreludeDicts.jlを使用する。）

#### コルーチンを使用した`modify!`に基づくトークンAPI

```jldoctest PreludeDicts
struct Token  # 簡単のためにフィールドを特化しない
    task::Task
    key::Any
    state::Union{Nothing,Pair}
end

function gettoken(dict, key)
    parent = current_task()
    task = @task begin
        y = modify!(dict, key) do state
            yieldto(parent, state)
        end
        yieldto(parent, y)
    end
    return Token(task, key, yieldto(task))
end

function Base.getindex(token::Token)
    state = token.state
    state === nothing && throw(KeyError(token.key))
    return last(state)
end

Base.setindex!(token::Token, value) = yieldto(token.task, Some(value))

dict = Dict()

tk = gettoken(dict, :a)
tk[] = 111

tk = gettoken(dict, :a)
tk[]
# 出力
111
```
