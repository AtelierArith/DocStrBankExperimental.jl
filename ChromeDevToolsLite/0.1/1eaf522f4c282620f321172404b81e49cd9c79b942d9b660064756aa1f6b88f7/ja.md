```
click(client::WSClient; button::String = "left", x::Union{Int, Nothing} = nothing,
    y::Union{Int, Nothing} = nothing, modifiers::Vector{String} = String[], verbose::Bool = false)
```

指定された座標または現在のマウス位置でマウスクリックアクションを実行します。

# 引数

  * `client::WSClient`: アクションを実行するWebSocketクライアント
  * `button::String="left"`: クリックするマウスボタン ("left", "right", "middle")
  * `x::Union{Int,Nothing}=nothing`: クリックのオプションのx座標
  * `y::Union{Int,Nothing}=nothing`: クリックのオプションのy座標
  * `modifiers::Vector{String}=String[]`: キーボード修飾キー (例: ["Shift", "Control"])
