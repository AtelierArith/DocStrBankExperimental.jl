```
@precompile_setup begin
    vars = ...
    ⋮
end
```

パッケージのプリコンパイル中のみコードブロックを実行します。 `@precompile_setup` はしばしば [`@precompile_all_calls`](@ref) と組み合わせて使用されます。例えば：

```
@precompile_setup begin
    vars = ...
    @precompile_all_calls begin
        y = f(vars...)
        g(y)
        ⋮
    end
end
```

`@precompile_setup` はコンパイルを強制するものではありません（ただし、そうなる可能性はあります）し、ランタイムディスパッチを意図的にキャプチャするものでもありません（ただし、ランタイム呼び出しがあなたのパッケージに属するメソッドの場合は、プリコンパイルされることになります）。
