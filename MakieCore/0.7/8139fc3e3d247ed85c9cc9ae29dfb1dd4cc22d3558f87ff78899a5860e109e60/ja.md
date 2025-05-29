すべてのバックエンドによって実装されたスクリーンコンストラクタ：

```julia
# プロットをウィンドウに表示することを目的としたコンストラクタ。
Screen(scene::Scene; screen_config...)

# png/jpegをファイルまたはioに保存するためのスクリーン
Screen(scene::Scene, io::IO, mime; screen_config...)

# `colorbuffer(screen, format)`に対して効率的なスクリーン
Screen(scene::Scene, format::Makie.ImageStorageFormat; screen_config...)
```

すべてのバックエンドによって実装されたインターフェース：

```julia
# オーバーロードする必要があります：
size(screen) # ピクセル単位のサイズ
empty!(screen) # スクリーンの状態を空にして再利用するか、閉じる

# オプション
wait(screen) # ウィンドウが開いている限り待機する

# Makieによって提供される：
push_screen!(scene, screen)
```
