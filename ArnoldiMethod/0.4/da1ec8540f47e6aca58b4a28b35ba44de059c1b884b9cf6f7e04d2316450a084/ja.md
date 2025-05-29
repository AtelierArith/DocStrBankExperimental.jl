```julia
partialschur!(A, arnoldi; start_from, initialize, nev, which, tol, mindim, maxdim, restarts) → PartialSchur, History
```

これは、事前に割り当てられた [`ArnoldiWorkspace`](@ref) インスタンスで動作する [`partialschur`](@ref) のバリアントです。これは以下のケースで便利です：

1. 初期の部分シュア分解を提供するため。この場合、`start_from` をシュアベクトルの数に設定し、`partialschur` はそこから続行します。シュアベクトルが1つだけの場合は、代わりにそれを `v1` として渡す方が簡単なことに注意してください。
2. Krylov部分空間の基底、ヘッセンベルグ行列、およびいくつかの一時的な配列のためにカスタム配列タイプを提供するため。
3. `partialschur` を繰り返し呼び出す際にアロケーションを避けるため。

最初の列 `arnoldi.V[:, 1]` にKrylov部分空間を誘導する初期ベクトルを提供することもできます。その場合、`initialize` を明示的に `false` に設定してください。

戻り値には、PartialSchur 構造体が `arnoldi.V` と `arnoldi.H` のビューを含むことに注意してください。コピーは作成されません。
