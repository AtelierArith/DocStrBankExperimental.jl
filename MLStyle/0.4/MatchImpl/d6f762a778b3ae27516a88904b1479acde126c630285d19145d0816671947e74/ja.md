```
@switch <item> begin
    @case <pattern>
        <action>
end
```

`MLStyle`が提供するパターンマッチングの実際の使用では、時には厄介なことがあります。これを解決するために、[`@when`](@ref)や、今では[`@switch`](@ref)もあります。

以下のコードは多くの点で愚かです：

```julia
var = 1
@match x begin
    (var_, _) => begin
        var = var_
        # いろいろなことをする
    end
end
```

まず第一に、[`@match`](@ref)でのキャプチャは外部変数をシャドウイングするだけですが、時にはそれらを変更したいだけです。

第二に、[`@match`](@ref)は式であり、`=>`の右側には式のみが許可され、そこに`begin end`を書くとコードのフォーマットが悪くなる可能性があります。

これらの問題に対処するために、`@switch`マクロを提案します：

```julia
julia> var = 1
1

julia> x = (33, 44)
(33, 44)

julia> @switch x begin
       @case (var, _)
           println(var)
       end
33

julia> var
33

julia> @switch 1 begin
       @case (var, _)
           println(var)
       end
ERROR: matching non-exhaustive, at #= REPL[25]:1 =#
```
