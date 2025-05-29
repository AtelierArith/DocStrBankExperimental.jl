`paramnames(μ)` は `μ` のパラメータの名前を返します。これは次の式と同等です。

```
paramnames(μ) == (keys ∘ params)(μ)
```

しかし、これは型のみに依存します。特に、デフォルトの実装は次の通りです。

```
paramnames(μ::M) where {M} = paramnames(M)
```

新しい `ParameterizedMeasure` は自動的に `paramnames` メソッドを持ちます。他の測定値に対しては、このメソッドはオプションですが、次のように定義することで追加できます。

```
paramnames(::Type{M}) where {M} = ...
```

`params` も参照してください。
