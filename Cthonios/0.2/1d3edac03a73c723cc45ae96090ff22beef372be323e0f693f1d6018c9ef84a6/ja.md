```julia
struct Domain{C, D, S, DBCs, DDofs, NBCs, NS, CPs} <: Cthonios.AbstractDomain
```

  * `coords::Any`
  * `dof::Any`
  * `sections::Any`
  * `dirichlet_bcs::Any`
  * `dirichlet_dofs::Any`
  * `neumann_bcs::Any`
  * `neumann_bc_sections::Any`
  * `contact_pairs::Any`

ドメインタイプは、bcs、セクションなどの情報を保持します。`DofManager`の未知のdofsは自動的に設定されないことに注意してください。`Domain`を設定した後は、`update_unknown_dofs!`を実行する必要があります。

`mesh` - 開いている`FileMesh`へのハンドル。 `dof` - `DofManager`オブジェクト。 `sections` - `SectionInternal`のセット。 `dirichlet_bcs` - `DirichletBCInternal`のセット。 `dirichlet_dofs` - dirichlet dofsを適用するためのdofsのセット。これは主に帳簿管理の目的のためです。
