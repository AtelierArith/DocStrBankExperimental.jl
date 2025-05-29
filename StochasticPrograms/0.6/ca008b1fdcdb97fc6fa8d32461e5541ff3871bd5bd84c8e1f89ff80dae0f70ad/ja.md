```
instantiate(stochasticmodel::StochasticModel,
            sampler::AbstractSampler,
            n::Integer;
            instantiation::StochasticInstantiation = UnspecifiedInstantiation(),
            optimizer = nothing,
            defer::Bool = false,
            kw...)
```

サイズ `n` のサンプルインスタンスを、二段階の `stochasticmodel` に格納されたモデルと提供された `sampler` を使用して生成します。オプションで `optimizer` を提供できます。明示的な `instantiation` が提供されていない場合、構造はオプティマイザによって誘導されます。構造はデフォルトで `Deterministic` です。
