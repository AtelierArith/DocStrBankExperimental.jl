```
function PatchBasedLinearSolver(
  biform::Function, 
  patch_space::FESpace, 
  space::FESpace;
  local_solver = LUSolver(),
  is_nonlinear = false,
  weighted = false
)
```

[`PatchBasedLinearSolver`](@ref)の基礎的なプロパティからインスタンスを返します。ローカルパッチシステムは`local_solver`で解決されます。`weighted`がtrueの場合、グローバル補正を計算するために重み付きパッチ集約を使用します。
