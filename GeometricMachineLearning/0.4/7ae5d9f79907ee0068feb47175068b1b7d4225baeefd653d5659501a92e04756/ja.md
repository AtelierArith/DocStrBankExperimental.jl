```
SymplecticAttentionQ
```

[`SymplecticAttention`](@ref)から派生した定数です。これは入力の$q$部分のみを変更します。

# コンストラクタ

```julia
SymplecticAttentionQ(M; symmetric::Bool, activation)
```

キーワードのデフォルトはtrueとGeometricMachineLearning.MatrixSoftmax()です。

活性化関数（[`MatrixSoftmax`](@ref)または[`VectorSoftmax`](@ref)のいずれか）を変更したいかもしれませんが、キーワード`symmetric`を`true`に設定する方がほとんどの場合は良いです。
