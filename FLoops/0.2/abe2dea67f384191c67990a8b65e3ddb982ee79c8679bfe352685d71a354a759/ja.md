```
@floop begin
    s₁ = s₁の初期化
    s₂  # 事前初期化された変数
    ...
    for x in xs, ...
        ...
    end
end
```

`@floop begin ... end` は（空である可能性のある）一連の代入または変数宣言（上記の`s₂`のような）を期待し、その後に`for`ループが続きます。

帰納変数がない場合、`begin ... end`は省略できます：

```
@floop for x in xs, ...
    ...
end
```

並列実行には [`@reduce`](@ref) を使用します：

```
@floop for x in xs, ...
    ...
    @reduce ...
end
```

`@floop` は `executor` 引数（`SequentialEx`、`ThreadedEx`、`DistributedEx`などのexecutorのインスタンスであるべき）または `nothing`（適切な並列executorを示す）を取ることもできます：

```
@floop executor for x in xs, ...
    ...
    @reduce ...
end
```

例については [`FLoops`](@ref) のモジュールドキュメントを参照してください。
