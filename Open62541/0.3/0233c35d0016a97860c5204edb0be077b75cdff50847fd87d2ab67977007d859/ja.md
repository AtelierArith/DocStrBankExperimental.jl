```
UA_MethodCallback_wrap(f::Function)
```

は、入力に対して動作するシンプルなJulia関数を、`UA_MethodCallback_generate`に供給するための正しい形式にラップします。

`f`は、以下のシグネチャを持つJulia関数でなければなりません：

```
f(input1::Any, input2::Any, input3::Any, ...) -> output::Union{Any, Tuple{Any, ...}}
```

ここで`Any`は原則として任意の型が許可されることを意味します。しかし、Open62541はCに基づいているため、対応するメソッドノードは*常に*特定の入力型の組み合わせでのみ動作するように構成されています。

メソッドノードに与えられた入力だけでなく、より大きな柔軟性が必要な場合は、`UA_MethodCallback_generate`を参照してください。

参照：

[`UA_MethodCallback_generate`](@ref)

[`JUA_Argument`](@ref)

[`JUA_Server_addNode`](@ref)

例：

```
function simple_hello(name, adjective)
    assembledstring = "Hello "*name*", you are "*adjective
    return assembledstring
end 
```

これは、2つの文字列を入力として受け取り、1つの文字列を出力する関数を期待するメソッドノードに添付できます。
