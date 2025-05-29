```
NotImplementedError(interface::String, method::String) <: Exception
```

指定された `interface` の一部である、与えられたメソッド（シグネチャを説明する `String` の形式）が実装されていないことを示します。

与えられたメソッドは `method(..., ::T, ...)` の形式である必要があり、ここで `...` は他の引数です。この例外によって表示されるメッセージは `T` に直接関連しているため、特定のサブタイプを示す必要はありません。

`MethodError` と比較して、`NotImplementedError` は「ここで呼び出すべきメソッドがあるはずだが、インターフェースを利用する開発者によって実装される必要がある」と伝えます。これは主に [`@required`](@ref) マクロを通じて使用され、メッセージ生成を自動的に処理します。

## 例

以下の例で `MethodError` がメソッドが呼び出されることを意図していないことを示している点に注意してください。

```jldoctest; filter = r"#unused#"
julia> using RequiredInterfaces: NotImplementedError

julia> abstract type Foo end

julia> bar(::Foo, ::Int) = throw(NotImplementedError("Foo", "bar(::T, ::Int)"))
bar (generic function with 1 method)

julia> struct Baz <: Foo end

julia> bar(Baz(), 1)
ERROR: NotImplementedError: 呼び出されたメソッドは `Foo` インターフェースのフォールバック定義の一部です。
あなたの型 `T <: Foo` のために `bar(::T, ::Int)` を実装してください。
Stacktrace:
 [1] bar(::Baz, ::Int64)
   @ Main ./none:1
 [2] top-level scope
   @ none:1

julia> bar(1, Baz())
ERROR: MethodError: no method matching bar(::Int64, ::Baz)
関数 `bar` は存在しますが、この引数の型の組み合わせに対して定義されたメソッドはありません。

最も近い候補は:
  bar(!Matched::Foo, !Matched::Int64)
   @ Main none:1

Stacktrace:
 [1] top-level scope
   @ none:1
```
