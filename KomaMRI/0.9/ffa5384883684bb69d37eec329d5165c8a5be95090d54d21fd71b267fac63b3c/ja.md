```
out = KomaUI(; kwargs...)
```

KomaのUIを起動します。

# キーワード

  * `darkmode`: (`::Bool`, `=true`) UIのダークモードスタイルを定義します
  * `frame`: (`::Bool`, `=true`) Blinkウィンドウの上部フレームを表示します
  * `phantom_mode`: (`::String`, `="2D"`, opts=[`"2D"`, `"3D"`]) デフォルトのファントムを2Dまたは3Dの脳の例として読み込みます
  * `sim`: (`::Dict{String,Any}`, `=Dict{String,Any}()`) シミュレーションパラメータの辞書
  * `rec`: (`::Dict{Symbol,Any}`, `=Dict{Symbol,Any}()`) 再構成パラメータの辞書
  * `return_window`: (`::Bool`, `=false`) `out`を'nothing'またはBlinkウィンドウのいずれかにします。これは、`return_window`キーワード引数がtrueに設定されているかどうかによります
  * `show_window`: (`::Bool`, `=true`) Blinkウィンドウを表示します

# 戻り値

  * `out`: (`::Nothing`または`::Blink.AtomShell.Window`) `return_window`キーワード引数がtrueに設定されているかどうかによって、'nothing'またはBlinkウィンドウのいずれかを返します。

# 例

```julia-repl
julia> KomaUI()
```
