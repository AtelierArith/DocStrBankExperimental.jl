```
@public name₁ name₂ … nameₙ
@public @macroname
```

現在のモジュールの公開API名を宣言します。

2番目の形式 `@public @macroname` は `@public var"@macroname"` と同等です。

# 拡張ヘルプ

このマクロが呼び出される場所が重要であることに注意してください。考えてみてください：

```julia
module A1
    using PublicAPI: @public
    @public B, C
    module B
        f() = nothing
    end
    module C
        using PublicAPI: @public
        using ..B: f
        @public f
    end
end
```

と

```julia
module A2
    using PublicAPI: @public
    @public B, C
    module B
        using PublicAPI: @public
        f() = nothing
        @public f
    end
    module C
        using ..B: f
    end
end
```

完全修飾名 `A1.C.f` と `A2.B.f` は公開されていますが、`A1.B.f` と `A2.C.f` はプライベートです。
