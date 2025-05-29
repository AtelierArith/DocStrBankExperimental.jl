```
@scachejld_if condition [[type] cache_dir] function_call
```

`function_call`の結果を`condition`が`true`の場合のみキャッシュします。

キャッシュされた結果が存在しても、読み込まれないことに注意してください。

他のパラメータのドキュメントについては[`@scachejld`](@ref)を参照してください。

## 例

```julia-repl
julia> using SimpleCaching

julia> SimpleCaching.settings.log = true;

julia> @scachejld_if true "cute-cube" "./" fill(0, 3, 3, 3)
● [ 2022-12-09 16:06:42 ] Computing cute-cube...
● [ 2022-12-09 16:06:42 ] Computed cute-cube in 0.009 seconds (00:00:00)
● [ 2022-12-09 16:06:44 ] Saving cute-cube to file ./cute-cube_4bbf9c2851f2c2b3954448f1a8085f6e3d40085add71f19640343885a8b7bd6a.jld[.tmp]...
3×3×3 Array{Int64, 3}:
[:, :, 1] =
 0  0  0
 0  0  0
 0  0  0

[:, :, 2] =
 0  0  0
 0  0  0
 0  0  0

[:, :, 3] =
 0  0  0
 0  0  0
 0  0  0

julia> @scachejld_if true "cute-cube" "./" fill(0, 3, 3, 3)
● [ 2022-12-09 16:07:04 ] Loading cute-cube from file ./cute-cube_4bbf9c2851f2c2b3954448f1a8085f6e3d40085add71f19640343885a8b7bd6a.jld...
3×3×3 Array{Int64, 3}:
[:, :, 1] =
 0  0  0
 0  0  0
 0  0  0

[:, :, 2] =
 0  0  0
 0  0  0
 0  0  0

[:, :, 3] =
 0  0  0
 0  0  0
 0  0  0

shell> ls -lh cute-cube_4bbf9c2851f2c2b3954448f1a8085f6e3d40085add71f19640343885a8b7bd6a.jld
-rw-r--r--. 1 user user 1000 9 dic 16.07 cute-cube_4bbf9c2851f2c2b3954448f1a8085f6e3d40085add71f19640343885a8b7bd6a.jld

```

しかし、`false`の`condition`を渡すと（読み込みログがないことに注意）：

```julia-repl
julia> @scachejld_if false "cute-cube" "./" fill(0, 3, 3, 3)
3×3×3 Array{Int64, 3}:
[:, :, 1] =
 0  0  0
 0  0  0
 0  0  0

[:, :, 2] =
 0  0  0
 0  0  0
 0  0  0

[:, :, 3] =
 0  0  0
 0  0  0
 0  0  0

```
