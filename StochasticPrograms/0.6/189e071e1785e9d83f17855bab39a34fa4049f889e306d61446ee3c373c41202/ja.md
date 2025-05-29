```
@sample(def)
```

@samplerブロック内でサンプル操作を定義し、次の構文を使用します。

```julia
@sample begin
    ...
    return sampled_scenario
end
```

サンプラーオブジェクトは予約語`sampler`を通じて参照され、内部のすべてにアクセスできます。
