```julia
@bind image WebcamInput(; kwargs...)
```

ウェブカメラ入力。ユーザーにカメラを選択し、写真を撮るための小さなインターフェースを提供し、キャプチャされた画像は `@bind` を介して `Matrix{RGB}` として返されます。

# `Matrix{RGB}` の使い方

出力タイプは `Matrix{RGB{N0f8}}` のタイプです。これを分解してみましょう：

  * `Matrix`: これは 2D **配列**で、`img[10,20]` のようにインデックスを付けて、`RGB{N0f8}` タイプのエントリを取得できます。
  * `RGB` ([ColorTypes.jl](https://github.com/JuliaGraphics/ColorTypes.jl) から): `r`（赤）、`g`（緑）、`b`（青）のフィールドを持つ `struct` で、各フィールドは `N0f8` タイプです。これらは色を構成するデジタル「チャネル」値です。
  * `N0f8` ([FixedPointNumbers.jl](https://github.com/JuliaMath/FixedPointNumbers.jl) から): 8ビットのみを使用する特別なタイプの浮動小数点数です。通常の `Float64` ではなく、`Float8` と考えてください。`Float64(x)` を使用して通常の `Float64` に変換できます。

デフォルトでは、`Matrix{RGB}` はテキストを使用して表示されますが、ノートブックのどこかに 

```julia
import ImageShow, ImageIO
```

を追加すると、Pluto はマトリックスをカラー画像として表示できるようになります。

画像操作機能の詳細については、[`Images.jl`](https://github.com/JuliaImages/Images.jl) をご覧ください。

# キーワード引数

  * `help::Bool=true` デフォルトでは、`WebcamInput` を使用するときに小さなヘルプメッセージを表示します。ここで無効にできます。
  * `default::Matrix{RGB{N0f8}}` デフォルトの画像を設定します。これはユーザーが画像をキャプチャするまで使用されます。デフォルトは **1x1 の透明な画像** です。
  * `max_size::Int64` 指定された場合、画像の最大寸法を制約し、アスペクト比を維持します。値が低いほどパフォーマンスが向上します。
  * `avoid_allocs::Bool=false` `true` に設定すると、生の `Vector{UInt8}` カメラデータを `AbstractMatrix{RGB{N0f8}}` に遅延変換し、ゼロアロケーションで行います。これによりパフォーマンスが向上しますが、バウンド値は `Matrix` ではなく `AbstractMatrix` になります。

# 例

```julia
@bind image WebcamInput()
```

キャプチャしたものを見てみましょう：

```julia
import ImageShow, ImageIO
```

```julia
image
```

マトリックスの **サイズ** を見てみましょう：

```julia
size(image)
```

画像の **右上** ピクセルの **緑** チャンネル値を取得するには：

```julia
image[1, end].g
```
