```julia
update_unknown_dofs!(domain::Cthonios.Domain, asm)

```

Update the unknown dofs in `domain.dof`,  `domain.dirichlet_dofs`, and `asm`. TODO maybe move `domain.dirichlet_dofs``to the`$DofManager$`in`$FiniteElementContainers$`.`$domain$`- Domain object.`$asm$` - Assembly object.
