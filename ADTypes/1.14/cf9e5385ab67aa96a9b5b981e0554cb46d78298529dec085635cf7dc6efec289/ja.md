```
AutoForwardDiff{chunksize,T}
```

自動微分のために[ForwardDiff.jl](https://github.com/JuliaDiff/ForwardDiff.jl)バックエンドを選択するために使用される構造体。

[ADTypes.jl](https://github.com/SciML/ADTypes.jl)によって定義されています。

# コンストラクタ

```
AutoForwardDiff(; chunksize=nothing, tag=nothing)
```

# 型パラメータ

  * `chunksize`: 一度に複数の導関数を評価するための推奨される[チャンクサイズ](https://juliadiff.org/ForwardDiff.jl/stable/user/advanced/#Configuring-Chunk-Size)

# フィールド

  * `tag::T`: ネストされた微分呼び出しを処理するための[カスタムタグ](https://juliadiff.org/ForwardDiff.jl/release-0.10/user/advanced.html#Custom-tags-and-tag-checking-1)（通常は必要ありません）
