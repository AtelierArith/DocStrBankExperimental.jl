```
function TransM(type)
    Union{Tuple{Symmetric{T,Array{T,2}},Array{T,1},Array{T,2}},
          Tuple{Symmetric{T,Array{T,2}},Array{T,2},Array{T,2}}} where T <: type
end
```

右エンサンブル異常変換、平均更新重み、および平均保存直交変換を伴うアンサンブル更新ステップを表すタプルの型ユニオンコンストラクタ。
