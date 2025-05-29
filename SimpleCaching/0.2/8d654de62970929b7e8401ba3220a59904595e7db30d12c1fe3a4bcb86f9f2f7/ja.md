```
@scachejld [[type] cache_dir] function_call
```

`function_call`の結果を`cache_dir`にキャッシュし、保存されたファイルのプレフィックスに`type`を付けます。

このマクロは、キャッシュファイルを保存および読み込むために`JLD2`の`@save`および`@load`マクロを使用するため、[`@scache`](@ref)マクロよりも遅く、メモリ効率が悪いです。`@scache`マクロは`serialize`を使用しますが、こちらは異なるJuliaバージョン間でのポータビリティが低くなります。

!!! note
    [`@scache`](@ref)と[`@scachejld`](@ref)の両方を使用する場合、ファイル拡張子は`.jld`になります。


!!! note
    `type`が省略された場合、関数名が`type`として使用されます。


!!! note
    `cache_dir`が省略された場合、[`SimpleCachingSettings`](@ref)の`cache_dir`フィールドに設定された値が使用されます。


## 例

```julia-repl
julia> using SimpleCaching

julia> SimpleCaching.settings.log = true;

julia> @scachejld "cute-cube" "./" fill(0, 3, 3, 3)
● [ 2022-12-09 15:56:09 ] Computing cute-cube...
● [ 2022-12-09 15:56:09 ] Computed cute-cube in 0.0 seconds (00:00:00)
● [ 2022-12-09 15:56:09 ] Saving cute-cube to file ./cute-cube_4bbf9c2851f2c2b3954448f1a8085f6e3d40085add71f19640343885a8b7bd6a.jld[.tmp]...
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

julia> @scachejld "cute-cube" "./" fill(0, 3, 3, 3)
● [ 2022-12-09 15:56:19 ] Loading cute-cube from file ./cute-cube_4bbf9c2851f2c2b3954448f1a8085f6e3d40085add71f19640343885a8b7bd6a.jld...
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

shell> ls -l cute-cube_4bbf9c2851f2c2b3954448f1a8085f6e3d40085add71f19640343885a8b7bd6a.jld
-rw-r--r--. 1 user user 1000  9 dic 15.56 cute-cube_4bbf9c2851f2c2b3954448f1a8085f6e3d40085add71f19640343885a8b7bd6a.jld

```

関数引数の式は最初のステップとして計算されるため、引数が異なってもキャッシュファイルが読み込まれ、同じ結果に評価されます。

```julia-repl
julia> @scachejld "cute-cube" "./" fill(0, 3, round(Int64, 1.5 * 2), 3)
● [ 2022-12-09 15:59:13 ] Loading cute-cube from file ./cute-cube_4bbf9c2851f2c2b3954448f1a8085f6e3d40085add71f19640343885a8b7bd6a.jld...
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
