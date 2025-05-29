```julia
update_unknown_dofs!(domain::Cthonios.Domain, asm)

```

`domain.dof`、`domain.dirichlet_dofs`、および`asm`の未知の自由度を更新します。TODO もしかしたら`domain.dirichlet_dofs`を`$DofManager$`に移動するかもしれません`$FiniteElementContainers$`。`$domain$` - ドメインオブジェクト。`$asm$` - アセンブリオブジェクト。
