```
@setup_workload begin
    vars = ...
    ⋮
end
```

パッケージのプリコンパイル中のみコードブロックを実行します。 `@setup_workload` はしばしば [`@compile_workload`](@ref) と組み合わせて使用されます。例えば：

```
@setup_workload begin
    vars = ...
    @compile_workload begin
        y = f(vars...)
        g(y)
        ⋮
    end
end
```

`@setup_workload` はコンパイルを強制することはありません（ただし、そうなることもあります）し、ランタイムディスパッチを意図的にキャプチャすることもありません（ただし、ランタイムコーラーがあなたのパッケージに属するメソッドの場合は、事前にコンパイルされます）。
