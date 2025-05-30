```julia
assemble_saddlepointmatrix_stokes(
    mesh::MinFEM.Mesh;
    alpha
) -> Any

```

離散化されたストークス方程式の解のためのinf-sup安定化を含む鞍点系行列を返します。
