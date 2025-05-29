```
SamePad()
```

畳み込み層（および関連するもの）にオプションとして渡されると、`stride==1` のときに入力サイズと出力サイズが一致するようにパディングが選択されます（最初の `N` 次元、カーネルまたはウィンドウ）。`stride≠1` の場合、出力サイズは `ceil(input_size/stride)` に等しくなります。

[`Conv`](@ref) や [`MaxPool`](@ref) も参照してください。

# 例

```jldoctest
julia> xs = rand32(100, 100, 3, 50);  # 画像のバッチ

julia> layer = Conv((2,2), 3 => 7, pad=SamePad())
Conv((2, 2), 3 => 7, pad=(1, 0, 1, 0))  # 91 パラメータ

julia> layer(xs) |> size  # このパディングで次元が同じままであることに注意
(100, 100, 7, 50)

julia> layer2 = Conv((2,2), 3 => 7)
Conv((2, 2), 3 => 7)  # 91 パラメータ

julia> layer2(xs) |> size  # パディングが「同じ」でなかったため出力次元が変わる
(99, 99, 7, 50)

julia> layer3 = Conv((5, 5), 3 => 7, stride=2, pad=SamePad())
Conv((5, 5), 3 => 7, pad=2, stride=2)  # 532 パラメータ

julia> layer3(xs) |> size  # 出力サイズ = `ceil(input_size/stride)` = 50
(50, 50, 7, 50)
```
