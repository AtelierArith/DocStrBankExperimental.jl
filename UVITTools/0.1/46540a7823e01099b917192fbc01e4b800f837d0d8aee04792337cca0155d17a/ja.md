uvit_countrate2flux(channel, filter, cps)

ネットソースカウントレートを、FUV/NUVの任意の広帯域フィルターに対するフラックス密度またはマグニチュードに変換します。この関数は`uvit_aphot.jl`で使用されます。

...

# 引数

  * `channel::String`: UVITチャネル FUVまたはNUV
  * `filter::String` : FUVまたはNUVフィルター 例: "BaF2".
  * `cps::Float64` : 秒あたりのカウント数。

...
