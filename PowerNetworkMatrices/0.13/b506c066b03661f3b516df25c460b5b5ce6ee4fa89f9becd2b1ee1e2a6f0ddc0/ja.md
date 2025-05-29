```julia
Ybus(branches, buses; ...)
Ybus(
    branches,
    buses,
    fixed_admittances;
    check_connectivity,
    make_branch_admittance_matrices
)

```

バスとブランチのコレクションからYbusを構築します。返されるのは、バス番号とブランチ名でインデックス付けされたYbus配列です。

# 引数

  * `check_connectivity::Bool`: 深さ優先探索（DFS）を使用してネットワークの接続性をチェックします。
