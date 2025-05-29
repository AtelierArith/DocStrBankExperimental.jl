```
@fgenerator function f(...) ... end
@fgenerator f(...) = ...
@fgenerator(generator::GeneratorType) do; ...; end
```

Transducers.jl互換のAPI（*foldable*インターフェース）で使用可能な「ジェネレーター」を返す関数`f`を定義します。`@fgenerator(generator::GeneratorType) do ... end`形式で、`GeneratorType`のためのTransducers.jlインターフェースを定義します。

関数本体でアイテムを生成するために[`@yield`](@ref)を使用します。アイテムの生成を終了するには`return`を使用します。

[`FGenerators`](@ref)も参照してください。

# 拡張ヘルプ

## 例

ジェネレーターを返す関数を定義する：

```jldoctest @fgenerator
julia> using FGenerators

julia> @fgenerator function generate123()
           @yield 1
           @yield 2
           @yield 3
       end;

julia> collect(generate123())
3-element Array{Int64,1}:
 1
 2
 3
```

既存の型のためのfoldableインターフェースを定義する：

```jldoctest @fgenerator
julia> struct Counting end;

julia> @fgenerator(itr::Counting) do
           i = 1
           while true
               @yield i
               i += 1
           end
       end;

julia> using Transducers  # for `Take`

julia> Counting() |> Take(3) |> collect
3-element Array{Int64,1}:
 1
 2
 3
```

`collect`や`sum`のような関数は、依然として`iterate`ベースのメソッドにディスパッチします（上記の`Counting`の例は、`Counting`が`Take`でラップされていたために機能しました）。`foldl`ベースのメソッドに自動的にディスパッチするには、スーパタイプとして`Foldable`を使用します：

```jldoctest @fgenerator
julia> struct Count <: Foldable
           start::Int
           stop::Int
       end;

julia> @fgenerator(itr::Count) do
           i = itr.start
           i > itr.stop && return
           while true
               @yield i
               i == itr.stop && break
               i += 1
           end
       end;

julia> collect(Count(0, 2))
3-element Array{Int64,1}:
 0
 1
 2
```
