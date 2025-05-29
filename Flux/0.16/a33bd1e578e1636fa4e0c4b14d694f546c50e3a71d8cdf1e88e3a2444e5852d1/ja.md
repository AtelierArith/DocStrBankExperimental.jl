```
GlobalMeanPool()
```

グローバル平均プーリング層。

(w,h,c,b) 形状の入力を (1,1,c,b) 形状の出力に変換し、完全な (w,h) 形状の特徴マップに対して平均プーリングを実行します。

```jldoctest
julia> xs = rand(Float32, 100, 100, 3, 50);

julia> m = Chain(Conv((3,3), 3 => 7), GlobalMeanPool());

julia> m(xs) |> size
(1, 1, 7, 50)
```
