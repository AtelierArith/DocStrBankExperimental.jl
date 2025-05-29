```
MetaSampler(::NamedTuple)
```

複数のサンプラーを含むNamedTupleをラップします。サンプリングされると、各サンプラーからのバッチを持つ名前付きタプルを返します。エポックごとに複数回サンプリングするアルゴリズムで内部的に使用されます。MetaSamplerでの単一の「サンプリング」は、内部サンプラーの数ではなく、Trajectoryコントローラーのカウントを1だけ増加させることに注意してください。これはエージェントを初期化する際に考慮する必要があります。

# 例

```
MetaSampler(policy = BatchSampler(10), critic = BatchSampler(100))
```
