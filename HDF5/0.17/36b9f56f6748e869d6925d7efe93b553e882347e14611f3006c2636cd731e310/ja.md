```
copyto!(output_buffer::AbstractArray{T}, obj::Union{DatasetOrAttribute}) where T
```

HDF5データセットまたは属性の[一部]を事前に割り当てられた出力バッファにコピーします。出力バッファはポインタに変換可能で、連続したレイアウトを持っている必要があります。
