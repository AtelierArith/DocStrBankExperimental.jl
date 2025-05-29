```
phantom = brain_phantom2D(;axis="axial", ss=4)
```

2次元脳ファントム構造体を作成します。デフォルトのss=4サンプル間隔は2 mmです。元のファイル（ss=1）のサンプル間隔は0.5 mmです。

# 参考文献

  * B. Aubert-Broche, D.L. Collins, A.C. Evans: "A new improved version of the realistic   digital brain phantom" NeuroImage, in review - 2006
  * B. Aubert-Broche, M. Griffin, G.B. Pike, A.C. Evans and D.L. Collins: "20 new digital   brain phantoms for creation of validation image data bases" IEEE TMI, in review - 2006
  * https://brainweb.bic.mni.mcgill.ca/brainweb/tissue*mr*parameters.txt

# キーワード

  * `axis`: (`::String`, `="axial"`, opts=[`"axial"`, `"coronal"`, `"sagittal"`]) ファントムの方向
  * `ss`: (`::Integer or ::Vector{Integer}`, `=4`) スカラーの場合はすべての軸のサブサンプリングパラメータ、2要素ベクトル[ssx, ssy]の場合は各軸のサブサンプリングパラメータ
  * `us`: (`::Integer or ::Vector{Integer}`, `=1`) スカラーの場合はすべての軸のアップサンプリングパラメータ、2要素ベクトル[usx, usy]の場合は各軸のアップサンプリングパラメータ、使用する場合はssがss=1に設定されます

# 戻り値

  * `obj`: (`::Phantom`) ファントム構造体

# 例

```julia-repl
julia> obj = brain_phantom2D(; axis="sagittal", ss=1)

julia> obj = brain_phantom2D(; axis="axial", us=[1, 2])

julia> plot_phantom_map(obj, :ρ)
```
