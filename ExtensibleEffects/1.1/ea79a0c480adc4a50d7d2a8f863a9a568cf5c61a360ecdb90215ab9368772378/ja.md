```
@insert_into_runhandlers outer_handler @syntax_eff begin
  # ...
end
```

単純なエフェクトは、プレーンな値に直接合成され、再びプレーンな値から再構築されることができますが、さらに文脈を提供しないと値を抽出できないいくつかのより複雑なエフェクトもあります。

コール可能なものは良い例です。コール可能なものの値を抽出することは、それを呼び出すか、またはそれを囲む別のコール可能なものを構築しない限り不可能です。

これらの例では、典型的なフローは次のようになります。

```julia

Callable(function (args...; kwargs...)
  callablehandler = CallableHandler(args...; kwargs...)

  SomeOtherNeededContext() do info
    otherhandler = SomeOtherHandler(info)

    # ... さらにネストされる可能性があります

    @runhandlers (callablehandler, otherhandler #= さらなるハンドラの可能性 =#) @syntax_eff begin
      # ...
    end
  end
end)
```

`@inser_into_runhandlers` は、これらの外部ハンドラを互いに分離し、合成可能な入れ替え可能なマクロとして使用できるようにするために使用できます。

例えば、ここでは `@runcallable` の実装（マクロの衛生を無視して）を示します。

```julia
macro runcallable(expr)
  :(Callable(function(args...; kwargs...)
    @insert_into_runhandlers(CallableHandler(args...; kwargs...), $expr)
  end))
end
```

これは、与えられた `expr` 内で既存の `runhandlers` への呼び出しを検索し、見つかった場合は、上記の動機付けの例に似た形で CallableHandler を挿入します。`runhandlers` が見つからない場合は、新しいものを作成します。

このようにして、ネストされたコード構造を非常に簡単に合成できます。常にすべての外部エフェクトを一度に、1つのステートメントで実行するように注意する必要があります。そうすれば、`@insert_into_runhandlers` が実際に正しい `runhandlers` を見つけることができます。
