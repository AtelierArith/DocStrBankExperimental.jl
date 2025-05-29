```julia
NyströmSkOp(
    m,
    X,
    ker;
    linop_type,
    sampling_type,
    ls_regularization,
    stability_shifting,
    use_falkon,
    out_dic
)

```

`NyströmSkOp`オブジェクトを（対称）カーネル`k`とデータセット`X`からランダムにサンプリングされた`m`ポイントを使用して作成します（サンプル = 列）。効率が求められる場合は、KernelFunctionsパッケージからのカーネルを使用することを強くお勧めします。
