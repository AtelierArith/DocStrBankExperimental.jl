```
GlobalMaxPool()
```

グローバルマックスプーリング層。

(w,h,c,b) 形状の入力を (1,1,c,b) 形状の出力に変換し、完全な (w,h) 形状の特徴マップに対してマックスプーリングを実行します。

[`MaxPool`](@ref) や [`GlobalMeanPool`](@ref) も参照してください。

```jldoctest
julia> xs = rand(Float32, 100, 100, 3, 50);

julia> m = Chain(Conv((3,3), 3 => 7), GlobalMaxPool());

julia> m(xs) |> size
(1, 1, 7, 50)

julia> GlobalMaxPool()(rand(3,5,7)) |> size  # 2次元を保持
(1, 5, 7)
```
