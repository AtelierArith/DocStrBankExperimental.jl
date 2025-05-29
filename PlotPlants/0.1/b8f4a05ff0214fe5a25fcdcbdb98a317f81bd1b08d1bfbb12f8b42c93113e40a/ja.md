```
create_canvas(
            id::Union{Int,String};
            ncol::Int = 1,
            nrow::Int = 1,
            axids::Array{Int,1} = Int[],
            figsize::Tuple{Number,Number} = (0.5+ncol*3, 0.5+nrow*3),
            dpi::Number = 100
)
```

キャンバスを作成します。与えられたものは

  * `id` 図のID
  * `ncol` 図の列数
  * `nrow` 図の行数
  * `axids` 図のサブプロットのインデックス
  * `figsize` 与えられたキャンバスサイズ
  * `dpi` 与えられたインチあたりのピクセル数
