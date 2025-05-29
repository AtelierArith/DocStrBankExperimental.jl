```
I = image_alpha!(img::GMTimage; alpha_ind::Integer, alpha_vec::Vector{Integer}, alpha_band::UInt8, burn=false)
```

GMTimageオブジェクト`img`のアルファ透明度を変更します。画像がインデックスされている場合、`alpha_ind=n`を使用して透明にする色インデックスを変更するか、範囲[0 255]の透明度値のベクトルを提供できます。このベクトルは元の色数よりも短くすることができます。真の色画像（RGB）のアルファを変更または追加するには`alpha_band`を使用します。

  * `burn`: 合成に使用される背景色です。範囲[0 255]の整数の3タプル、または色名になるシンボルまたは文字列であることができます。*例*、`bg=:blue`。デフォルトは`:white`です。このオプションは真の色画像と`alpha_band`にのみ使用可能です。その場合、アルファバンドを追加するのではなく、そのバンドは背景色を置き換えたり合成したりするために使用されます（アルファバンドの値が0または255以外の変数である場合）。

### 例

```jldoctest
# 例1: cmapの3番目の色を新しい透明色として変更
julia> image_alpha!(img, alpha_ind=3)

# 例2: cmapの最初の6色をランダムな値に割り当てて変更
julia> image_alpha!(img, alpha_vec=round.(Int32,rand(6).*255))

# ランダムな画像の赤色を焼く
julia> img = mat2img(rand(UInt8, 750, 750, 3));
julia> mask = rand(Bool, 750, 750);
julia> image_alpha!(img, alpha_band=mask, burn=:red);
```
