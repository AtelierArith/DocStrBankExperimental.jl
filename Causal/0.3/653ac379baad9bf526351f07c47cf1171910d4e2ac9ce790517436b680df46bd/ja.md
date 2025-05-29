```julia
initialize!(model, clock)

```

`model`を初期化し、`model`の各コンポーネントのためにコンポーネントタスクを起動します。ペアのコンポーネントとコンポーネントタスクは、`model`のタスクマネージャに記録されます。`model`の時計は[`set!`](@ref)され、[`Writer`](@ref)のファイルが開かれます。
