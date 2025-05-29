```
space_index(::Val{:index}, jd::Number; kwargs...) -> Number
space_index(::Val{:index}, date::DateTime; kwargs...) -> Number
```

ジュリア日 `jd` または `instant` のためのスペース `index` を取得します。後者は `DateTime` 型のオブジェクトでなければなりません。`kwargs...` はスペースインデックスの追加設定を渡すために使用できます。
