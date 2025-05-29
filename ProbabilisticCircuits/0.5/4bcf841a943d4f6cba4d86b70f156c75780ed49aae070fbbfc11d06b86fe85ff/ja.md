```
loglikelihood(root::ProbCircuit, data::Matrix, example_id; Float=Float32)
```

単一のインスタンス `data[example_id, :]` に対して、CPU上で再帰的に周辺対数尤度を計算します。

**注意**: 非常に遅いため、デモや教育目的でのみ使用してください。
