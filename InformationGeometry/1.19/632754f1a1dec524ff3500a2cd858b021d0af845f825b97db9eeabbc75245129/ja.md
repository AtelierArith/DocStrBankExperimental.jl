```
ViewElements(Inds::Union{AbstractArray, Tuple, Colon, Int}) -> Function
```

構造体内にラップされた配列のインデックスを表示するための関数 `X::AbstractArray{<:Number}->view(X, Inds)` を生成します。これにより、より情報豊富なスタックトレースが得られます。
