```
plot_unitary_populations(
    traj::NamedTrajectory;
    unitary_columns::AbstractVector{Int}=1:2,
    unitary_name::Symbol=:Ũ⃗,
    control_name::Symbol=:a,
    kwargs...
)
```

トラジェクトリ内のユニタリ行列のユニタリ列の集団をプロットします。`kwargs`は[`NamedTrajectories.plot`](https://docs.harmoniqs.co/NamedTrajectories/dev/generated/plotting/)に渡されます。

# キーワード引数

  * `unitary_columns::AbstractVector{Int}`: 集団をプロットするユニタリ行列の列。デフォルトは`1:2`です。
  * `unitary_name::Symbol`: トラジェクトリ内のユニタリ行列の名前。デフォルトは`:Ũ⃗`です。
  * `control_name::Symbol`: トラジェクトリ内の制御の名前。デフォルトは`:a`です。
  * `kwargs...`: [`NamedTrajectories.plot`](https://docs.harmoniqs.co/NamedTrajectories/dev/generated/plotting/)に渡される追加のキーワード引数。
