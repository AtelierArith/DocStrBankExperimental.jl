```
@scache [[type] cache_dir] function_call
```

`function_call`の結果を`cache_dir`ディレクトリにキャッシュし、保存されたファイルに`type`をプレフィックスとして付けます。

このマクロは`Serialize`の`serialize`および`deserialize`関数を使用してキャッシュファイルを保存および読み込むため、`JLD2`を使用する[`@scachejld`](@ref)マクロよりも高速でメモリ効率が良いです。一方、`@scachejld`は異なるJuliaバージョン間でのポータビリティが高いです。

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

julia> @scache "cute-cube" "./" fill(0, 3, 3, 3)
● [ 2022-12-09 15:39:42 ] Computing cute-cube...
● [ 2022-12-09 15:39:42 ] Computed cute-cube in 0.009 seconds (00:00:00)
● [ 2022-12-09 15:39:44 ] Saving cute-cube to file ./cute-cube_4bbf9c2851f2c2b3954448f1a8085f6e3d40085add71f19640343885a8b7bd6a.jld[.tmp]...
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

julia> @scache "cute-cube" "./" fill(0, 3, 3, 3)
● [ 2022-12-09 15:39:56 ] Loading cute-cube from file ./cute-cube_4bbf9c2851f2c2b3954448f1a8085f6e3d40085add71f19640343885a8b7bd6a.jld...
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
-rw-r--r--. 1 user user 232  9 dic 15.39 cute-cube_4bbf9c2851f2c2b3954448f1a8085f6e3d40085add71f19640343885a8b7bd6a.jld

```

関数引数の式は最初のステップとして計算されるため、引数が異なってもキャッシュファイルは読み込まれ、同じ結果に評価されます。

```julia-repl
julia> @scache "cute-cube" "./" fill(0, 3, parse(Int, "3"), 3)
● [ 2022-12-09 09:41:54 ] Loading cute-cube from file ./cute-cube_4bbf9c2851f2c2b3954448f1a8085f6e3d40085add71f19640343885a8b7bd6a.jld...
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
