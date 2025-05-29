```
QXTensor(data::AbstractArray{Elt, N},
         indices::Array{<:Index, 1};
         diagonal_check::Bool=true) where {Elt, N}
```

与えられたデータとインデックスを使用してQXTensorインスタンスを作成するためのコンストラクタです。diagonal*checkがtrueの場合、どのインデックスがハイパーインデックスであるかを自動的にチェックし、hyper*indicesフィールドに記録します。
