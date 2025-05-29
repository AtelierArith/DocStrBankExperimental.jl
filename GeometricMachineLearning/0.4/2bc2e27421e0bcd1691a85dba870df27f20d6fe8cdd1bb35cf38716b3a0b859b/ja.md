```
SymplecticAttentionP
```

[`SymplecticAttention`](@ref)から派生した定数です。これは入力の`p`部分のみを変更します。

# コンストラクタ

```julia
SymplecticAttentionP(M; symmetric::Bool, activation)
```

キーワードのデフォルトはtrueとGeometricMachineLearning.MatrixSoftmax()です。

活性化関数（[`MatrixSoftmax`](@ref)または[`VectorSoftmax`](@ref)のいずれか）を変更したいかもしれませんが、キーワード`symmetric`を`true`に設定する方がほとんどの場合は良いです。
