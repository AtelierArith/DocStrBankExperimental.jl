```
function ArView(type)
    Union{Array{T, 2}, SubArray{T, 2}} where T <: type
end
```

アンサンブル条件付け操作、統合スキーム、およびその他の配列操作で使用するための配列とサブ配列のユニオンの型コンストラクタ。
