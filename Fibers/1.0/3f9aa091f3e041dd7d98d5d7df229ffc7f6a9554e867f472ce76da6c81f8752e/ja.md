```
MRI(ref::MRI{A}, nframes::Integer=ref.nframes, datatype::DataType=eltype(A)) where A<:AbstractArray
```

参照 `MRI` 構造体 `ref` に基づいてヘッダーフィールドが populated された `MRI` 構造体を返し、画像配列はゼロで populated されます。

オプションとして、新しい `MRI` 構造体は参照 MRI 構造体とは異なるフレーム数 (`nframes`) で作成することができます。
