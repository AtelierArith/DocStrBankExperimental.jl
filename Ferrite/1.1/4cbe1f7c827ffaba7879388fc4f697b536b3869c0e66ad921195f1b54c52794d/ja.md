```
VTKGridFile(filename::AbstractString, grid::AbstractGrid; kwargs...)
VTKGridFile(filename::AbstractString, dh::DofHandler; kwargs...)
```

非構造のVTKグリッドを含む`VTKGridFile`を作成します。キーワード引数は`WriteVTK.vtk_grid`に渡されます。詳細は[データフォーマットオプション](https://juliavtk.github.io/WriteVTK.jl/stable/grids/syntax/#Data-formatting-options)を参照してください。

このファイルハンドラは、次のデータを書き込むために使用できます。

  * [`write_solution`](@ref)
  * [`write_cell_data`](@ref)
  * [`write_projection`](@ref)
  * [`write_node_data`](@ref).
  * [`Ferrite.write_cellset`](@ref)
  * [`Ferrite.write_nodeset`](@ref)
  * [`Ferrite.write_constraints`](@ref)

ファイルハンドラに書き込んだ後、データを保存するには`close(::VTKGridFile)`を呼び出す必要があります。サポートされている`do`ブロックを使用すると、これが自動的に行われます：

```julia
VTKGridFile(filename, grid) do vtk
    write_solution(vtk, dh, u)
    write_cell_data(vtk, celldata)
end
```
