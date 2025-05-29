```
MultiBatchSampler(sampler, n)
```

サンプラーをラップします。サンプリング時に、サンプラーを使用して n バッチをサンプリングします。MetaSampler と組み合わせることで、サンプラー間で異なるサンプリングレートを許可するのに便利です。MultiBatchSampler での単一の「サンプリング」は、Trajectory コントローラのカウントを 1 増加させるだけであり、`n` ではありません。これはエージェントを初期化する際に考慮する必要があります。

# 例

```
MetaSampler(policy = MultiBatchSampler(BatchSampler(10), 3),
            critic = MultiBatchSampler(BatchSampler(100), 5))
```
